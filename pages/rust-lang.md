# Rust

- immutable/mutable variable:
`let / let mut`

- immutable/mutable reference:
`&var / &mut var`

- A::b
b is an associated function of type A (= static method in other languages)

- can shadow immutable variables (with subsequent let).
Allows changing type with same name
Compared to mut, allows to do a few changes but then stay immutable

- 10_000, 0xff, 0o77, 0b1111_0000, b'A' (byte)

- integer overflow: panic when compiled in debug mode, overflows in release mode.
Considered an error to rely on overflow implicitly. Better use one of: wrapping_*, checked_*, overflowing_*, saturating_*

- default integer type = i32, default float type = f64

- single quotes = character, double quotes = string

- character = 4 bytes, Unicode Scalar Value (but Strings only take as many bytes as needed per char)

- Tuples
`let tup = (1, 'A', 1.2); let (x, y, z) = tup; let first = tup.0;`

- Arrays
`let array = [1, 2, 3];`
`for element in array.iter()`
Same type, can't change size (contrary to vector), goes to stack (vectors go to heap)
`let array: [i32; 3] = [1, 2, 3];`
`let array = ['A'; 3]; -> ['A', 'A', 'A']`
`let first = array[0];`
runtime check for out-of-bounds access

- Statements and expressions
Assignment is a statement, not an expression
Interestingly, blocks are expressions, e.g. { let x = 3; x + 1 } (note absence of semicolon) is an expression the value of which is 4
So return statements are not strictly necessary
if is also an expression: let x = if condition { 1 } else { 2 };

- return a value from a loop:
`break {{value}};`

- if nothing is returned (by a function or block), an empty tuple () is returned

- if/else must get a bool

- infinite loop:
`loop { ... }`

- for loops
`for n in (1..4)`
`for n in (1..4).rev()`

- Ownership and borrowing (matters for the heap. Role of garbage collection)
1. Each value in Rust has a variable that’s called its owner.
2. There can only be one owner at a time.
3. When the owner goes out of scope, the value will be dropped (Rust calls the object's drop method)
`let s1 = String::from("hello");`
`let s2 = s1;`
-> Now s1 is no longer valid. It's called a move.
Do a deep copy: s1.clone()
Not the case for e.g. integers, because then they're really copied on the stack.
They implement the Copy trait. Mutually exclusive with the Drop trait (what to do on going out of scope).
function calls take ownership, return statements give it
But having to return values all the time is tedious, so references exist (&s). Having references as function parameters is called borrowing. But then can't modify the object!
So can create mutable references (fn change(s: &mut String) {...}; change(&mut s)). But can only have one mutable reference to a particular object in a particular scope!
Solves data races since there are never 2 places allowed to modify some data at the same time.
We *also* cannot have a mutable reference while we have an immutable one (users of an immutable reference don’t expect the values to suddenly change out from under them). So there can be multiple readers, or 1 reader/writer.
A reference’s scope starts from where it is introduced and continues through the last time that reference is used (so different from traditional block scope).
A slice is a reference to part of an array (&s[1..5], &s[..5], &s[1..], &s[..]) (internally, consist in a pointer to the start of the slice, and a length)

- string slice type:
`&str`
- array slice type:
`&[{{i32}}]`
- string literals (let s = "string") are actually string slices (type &str), i.e. immutable references to strings (somewhere in the binary)

- structs and enums
Useful to create new types. structs = Ocaml product types; enums = Ocaml sum types

- fields in structs are private by default.

- field init shorthand for structs:
`fn build_user(email: String) -> User {`
`    User {`
`        email, (shortcut for email: email)`
`        active: true,`
`    }`
`}`

- struct update syntax:
`let user2 = User {`
`    email: String::from("another@example.com"),`
`    ..user1`
`};`

- tuple structs (structs with unnamed fields):
`struct Point(i32, i32, i32);`
`let p = Point(0, 1, 2);`

- unit-like structs: structs without any field. To create types with no associated data.

- format string: {} for types that implement the Display trait, {:?} for Debug

- defining a method on a type (then used with r.area())
`struct Rectangle {`
`    width: u32,`
`    height: u32,`
`}`
`impl Rectangle {`
`    fn area(&self) -> u32 {`
`        self.width * self.height`
`    }`
`}`

- associated function:
also inside the `impl`, but not taking self as argument (for namespacing). Then used as Rectangle::function()

- Rust makes borrowing implicit for method callers, with "automatic referencing and dereferencing":
when you call a method with object.something(), Rust automatically adds in &, &mut, or * so object matches the signature of the method

- enums
`enum IpAddrKind { V4, V6, }`
`let four = IpAddrKind::V4;`
`enum IpAddr { V4(String), V6(String), }`
`let home = IpAddr::V4(String::from("127.0.0.1"));`
An enum variant can contain any type (even another enum).

- the Option enum
Avoids the error-prone null value. It's better than null because Option<T> and T are not the same type. Defined like this:
`enum Option<T> { Some(T), None, }`
`let some_number = Some(5);`
`let absent_number: Option<i32> = None;`

- match
`match {{expr}} {`
`    {{pattern1}} | {{pattern2}} => {`
`        {{expr}}`
`    }`
`    {{pattern3}} => {{expr}},`
`    {{pattern4}} if {{match-guard-condition}} => {{expr}},`
`    {{pattern5}} | {{pattern6}} if {{match-guard-applies-to-both-patterns}} => {{expr}},`
`    {{1}}..={{5}} => {{println!("one through five")}}, // for chars and numeric values`
`}`
As in OCaml, matches must be exhaustive. Placeholder for all remaining cases:
`_ => {{()}},`
Concise syntax for when we're only interested in one arm of the match: if let (loses exhaustiveness check, except if followed with else)
`if let {{Some(3)}} = my_option_variable { {{...}} }`
(can be followed by unrelated `else if` and `else if let` conditions)
There's also `while let`.

- crate = a tree of modules that produces a library or executable
- package = one or more crates that provide a set of functionality
- module =
`mod { {{module code (functions, etc)}} }`

- src/main.rs, src/lib.rs are conventions for Cargo (sets them as roots of binary (resp library) crate).

- In a module, everything is private by default. Public function:
`pub fn {{...}}`

- relative paths to modules can start with `super::`

- add modules into scope:
`use {{path-to-module}} [as {{...}}]`
`use std::{cmp::Ordering, io};`
`use std::io::{self, Write};`
`use std::collections::*;`
(can also add a function directly into scope but not idiomatic. It's idiomatic for structs, enums, etc, though.)

- re-exporting (making items available in scope, and also to users of the library) (allows to write code with one structure, but expose another structure that might be more intuitive for users):
`pub use {{...}}`
(users can then use both structures as they wish)

- tell Rust to load the contents of a module from a file or directory with the same name:
`mod {{module}};`

- list of values (of the same type) that might change in size, in the heap: vector.

- strings
2 types: owned `String`, borrowed string slice `&str`, both UTF-8 encoded
Also in std lib: OsString, OsStr, CString, CStr
`String::from("foo") == "foo".to_string()`

- Strings can be concatenated with + (if s1 and s2 are of type String):
`let s3 = s1 + &s2;`
(uses deref coercion, to convert the given &String to the expected &str (converts &s2 to &s2[..]))

- alternative for string concatenation: format!

- String indexing isn't supported (want byte? scalar value? grapheme cluster?); String slices (e.g. &mystr[0..1]) can cause runtime panic if don't match grapheme boundaries.

- extract characters (scalar values) from a string: "नमस्ते".chars(). extract bytes: "नमस्ते".bytes(). extract graphemes: not in std lib.

- hash maps become the owner of their keys and values

- iterate over hash map:
`for (key, value) in &{{hash_map}} { {{...}} }`

- 2 kinds of errors: unrecoverable (panic!) and recoverable (Result<T, E>)

- panic!:
by default Rust unwinds and cleans up the stack before exiting. Can be configured to abort.
is how a test is marked as failing
can be used (via unwrap()) when we know failure is impossible, but the compiler doesn't.
Or when the caller of a function has violated the function's contract.
Or inside custom types, for validation.

- Result<T, E>
`enum Result<T, E> {`
`    Ok(T),`
`    Err(E),`
`}`

- useful methods on Result<T, E>:
unwrap_or_else() (take Ok value or return specified expression)
unwrap() (take Ok value or panic!)
expect() (like unwrap() but allows to specify the panic! error message)

- shortcut to propagate recoverable errors to calling function: the question mark
`{{function_that_returns_Result<T,E>}}()?;`
`File::open("hello.txt")?.read_to_string(&mut s)?;`
(well, there's fs::read_to_string() for that)
(takes care of error type conversion automatically)

- generic types: abstract stand-ins for concrete types or other properties

- traits: define behavior in a generic way. Allow to constrain a generic type only to types that have a particular behavior.

- syntax for a generic function:
`fn largest<T>(list: &[T]) -> T { ... }`
restricting to some trait:
`fn largest<T: std::cmp::PartialOrd>(list: &[T]) -> T {`

- generic struct:
`struct Point<T> { x: T, y: T, }`
etc.

- generic implementation:
`impl<T> Point<T> { ... }`

- specific implementation of generic type:
`impl Point<f32> { ... }`

- using generics has no runtime performance penalty, due to monomorphization: the compiler looks at all uses of the generic type, and creates the associated specific functions.

- traits:
define the behavior of a type.
`pub trait {{Summary}} {`
`    fn {{summarize(&self) -> String;}}`
Or can define a default implementation.
A default implementation can call methods that do not have a default implementation.
A default implementation can only be kept or overriden, not extended (i.e. not called from overriding implementation).
Then
`impl Summary for {{NewsArticle}} {`
`    fn summarize(&self) -> String { ... }`
`}`
Or if we want to use the default implementation:
`impl Summary for {{NewsArticle}} {}`
Can implement a trait on a type only if either the trait or the type is local to our crate. Can’t implement external traits on external types. Otherwise two crates could implement the same trait for the same type and Rust wouldn't know which one to use (so-called coherence).
Then to specify an argument must implement some trait:
`pub fn notify(item: &impl Summary) { ... }`
above is syntactic sugar for
`pub fn notify<T: Summary>(item: &T) { ... }`
Several traits:
`pub fn notify(item: &(impl Summary + Display)) { ... }`
`pub fn notify<T: Summary + Display>(item: &T) { ... }`
"where" syntax, to de-clutter function signatures:
`fn some_function<T: Display + Clone, U: Clone + Debug>(t: &T, u: &U) -> i32 { ... }`
becomes
`fn some_function<T, U>(t: &T, u: &U) -> i32`
`    where T: Display + Clone,`
`          U: Clone + Debug`
`{ ... }`
Can also conditionally implement methods on a type (e.g. struct Pair<T>):
`impl<T: Display + PartialOrd> Pair<T> {`
`    fn cmp_display(&self) { {{function that needs the Display and PartialOrd traits}} }`
Or conditionally implement methods on any type that has a trait ("blanket implementations"):
`impl<T: Display> ToString for T {`

- lifetimes:
Every reference has a lifetime: the scope for which that reference is valid. Lifetimes are inferred most of the time (like types), but sometimes we need to help the compiler (for functions or structs that use references). Lifetime annotations don't change lifetimes, they only help the compiler understand how different lifetimes relate to each other.
A reference is valid if the reference's lifetime is included in the data's lifetime.
`&i32        // a reference`
`&'a i32     // a reference with an explicit lifetime`
`&'a mut i32 // a mutable reference with an explicit lifetime`
An explicit lifetime annotation means "the reference lives at least as long as this lifetime".
A function specifying that all the references in its signature have the same lifetime:
`fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {`
If a struct holds a reference, it must also use lifetime annotations:
`struct ImportantExcerpt<'a> {`
`    part: &'a str,`
The Rust compiler has lifetime elision rules that allow to omit lifetime annotations for common programming patterns.
Special lifetime: 'static. All string literals ("string literal") have this lifetime.

- tests:
A function is a test if it's preceded by `#[test]`.
Doc-tests: rust can compile examples in the documentation so the code and documentation stay in sync!!
A test fails if something in it calls panic!, or if it returns an error.
Useful macros: assert_eq!, assert_ne!, assert!
To assert something should panic: #[should_panic] before the test function, or
`#[should_panic(expected = "{{expected error message substring}}")]`
Mark tests as ignored (because they take a lot of time so we only want to execute them occasionally):
`#[ignore]`
Unit tests go in the same file that they test, by convention, in a module usually named `tests` and annotated by `#[cfg(test)]`.
Integration tests are placed in the `tests` directory. Each file there is compiled to its own crate by `cargo test`. The `tests/common/mod.rs` convention can be used to share helper functions across integration tests.
Binary crates don't support integration tests. So people often write a straightforward `src/main.rs` and put the logic in `src/lib.rs`, to be able to test it.

- closures:
syntax:
`let my_closure = |param1, param2| { {{...}} }`
Type annotations are possible but not required, as the closure is not part of the external interface of a program and the compiler can infer the types from calls to the closure.
Each closure has its own anonymous unique type. But all closures implement at least one of these traits: Fn, FnMut, FnOnce (depending on how they take ownership of their captured environment):
- FnOnce: takes ownership (use the `move` keyword before the parameter list of the closure)
- FnMut: mutably borrows
- Fn: immutably borrows
Memoization of closures: we can use structs with a `calculation` field that holds the closure, and a `value` field (a hashmap) that holds the result for each already supplied argument(s).

- iterators:
are lazy, e.g.: v1.iter().map(|x| x + 1); -> nothing has happened yet, until we call e.g. collect()
Are a zero-cost abstraction (as fast as loops).
iterator over immutable references:
`{{seq}}.iter()`
over mutable references:
`{{seq}}.iter_mut()`
over owned values:
`{{seq}}.into_iter()`
common use of closures that capture their environment: the `filter` iterator adaptor.

- documentation comments (translated to HTML; support markdown, cargo test will run the code examples they contain):
`///`
The above syntax is for code items that are below the comment. To document the enclosing code (typically crates and modules):
`//!`

- crates.io is a bit harsh with published code: it can never be deleted... (to avoid breaking dependencies). Can `cargo yank` to prevent new projects from relying on a version though.

- code can be organized in workspaces: https://doc.rust-lang.org/book/ch14-03-cargo-workspaces.html

- smart pointers:
usually implemented using structs. They implement the `Deref` and `Drop` traits.
The `Deref` trait allows to use smart pointers like regular references, and notably to dereference them with `*`.

- Box<T> for allocating values on the heap:
useful in particular for recursive types

- Deref coercion:
a feature of Rust on types that implement the Deref trait, converting these types to a reference to another type they don't match the function or method signature. Allows to write simpler code.

- force a value to be dropped early, before the end of its scope (e.g. to release a lock):
`std::mem::drop({{value}})`
(can't call value.drop() directly)

- Rc<T>, a reference counting type that enables multiple ownership
e.g. in a graph, each node can be owned by multiple edges
Only for single-threaded scenarios. And only with immutable references.
Rc::clone() doesn't do a deep copy, it only increments the reference count.

- interior mutability pattern:
allows to mutate data even when there are immutable references to the data. Unsafe code, wrapped in safe APIs.
When we know that the borrowing rules will be respected at runtime, but the compiler can't.
Fundamentally, it's an immutable value but which can mutate itself from the inside.
e.g. RefCell<T>. Its API is safe in the sense that if we try to have a mutable borrow and immutable borrows at the same time, or multiple mutable borrows, the code will panic (RefCell<T> keeps track of its borrows at runtime).
Can be combined with Rc<T> to have multiple owners of mutable data.

- reference cycles can leak memory:
Rust does not offer absence of memory leak as one of its guarantees. It is difficult but possible to create them with e.g. Rc<T> and RefCell<T>, arranged in a cycle.
Solution: use Weak<T>. An Rc<T> has a strong count, which must be zero for the memory to be released, but also has a weak count which doesn't have to be zero. So to be used, a Weak<T> must first check whether what it's pointing to still exists. Example use: a tree where parents know about their children, and children know about their parents -> parent->children with Rc<T>, and children->parent with Weak<T>.

- fearless concurrency:
`thread::spawn({{closure}})`
By default all threads are killed when the main thread exits
`move` is commonly used with the closure to transfer ownership to the newly created thread

- message passing concurrency:
Rust supports the message passing paradigm to communicate between threads, with `std::sync::mpsc::channel()` (mpsc = multiple producers single consumer)
Channels transfer ownership from the sender to the receiver.

- shared state concurrency:
typically mutexes.
The data is inside a Mutex<T> type, so we can't forget to acquire the lock. And the lock release happens automatically when the variable that took the lock goes out of scope.
Rc<T> is not thread-safe (doesn't implement the `Send` trait), there's Arc<T> for that (atomic reference counting) (has a performance penalty, so Rc<T> is better in single-threaded contexts)
Mutex<T> does not protect against deadlocks.

- Send trait:
signals the type's ownership can be transferred between threads.

- Sync trait:
signals the type can be safely referenced from multiple threads (i.e. T is `Sync` if &T is `Send`).
Almost all types implement `Send`/`Sync`, and types composed of `Send`/`Sync` subtypes are automatically `Send`/`Sync` as well.

- OOP:
Rust's structs have methods, so they're like objects. They can also expose a limited public API (hide fields).
It doesn't have inheritance though. What's the reason for wanting inheritance?
-> if it's code sharing, can use default trait method implementations instead.
-> if it's for polymorphism (being able to work on several types), use type generics and traits.

- to have heterogeneous collections, see: https://doc.rust-lang.org/book/ch17-02-trait-objects.html. "Trait objects". Basically duck typing at runtime. Performance penalty of course.
(generic types with traits don't work because they must monomorphized at compile time)

- patterns
function parameter lists can contain patterns (like destructuring tuples).
destructuring a struct:
`let p = Point { x: 0, y: 7 };`
`let Point { x: a, y: b } = p;`
-> use vars a and b
`let Point { x, y } = p;`
As in OCaml, destructuring match:
`match p {`
`    Point { x, y: 0 } => println!("On the x axis at {}", x),`
`    Point { x: 0, y } => println!("On the y axis at {}", y),`
`    Point { x, y } => println!("On neither axis: ({}, {})", x, y),`
`}`
Destructuring can be nested and complicated.
`_` is to ignore a value, `..` is to ignore the remaining values (well, expands to as many values as needed, but doesn't need to be at the end):
`let numbers = (2, 4, 8, 16, 32);`
`match numbers {`
`    (first, .., last) => {`
`        println!("Some numbers: {}, {}", first, last);`
`    }`
`}`

- `_varname` to tell the compiler it's unused on purpose

- @ syntax: bind to a variable while testing the value in a pattern matching:
`enum Message {`
`    Hello { id: i32 },`
`}`
`let msg = Message::Hello { id: 5 };`
`match msg {`
`    Message::Hello {`
`        id: id_variable @ 3..=7,`
`    } => println!("Found an id in range: {}", id_variable),`
`    Message::Hello { id: 10..=12 } => {`
`        println!("Found an id in another range")`
`    }`
`    Message::Hello { id } => println!("Found some other id: {}", id),`
`}`

- unsafe Rust
why: because sometimes we know we're right but the compiler is too conservative; because we can want to do inherently unsafe low-level programming; because we want to call functions from another programming language (FFI)...

- TODO: basically the final chapter on advanced topics

- nice:
`unimplemented!({{msg}})`
