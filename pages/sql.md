# sql

- select by string equality:
`select * from {{table}} where '{{string}}' like {{column-name}};`

- rename a table:
`alter table {{table}} rename to {{new-name}};`

- create a new table from the result of a query:
`create table {{table}} as {{query}};`

- insert the result of a query in a table:
`insert into {{table}} {{query}};`

- create an index:
`create [unique] index {{name}} on {{table}} [using hash] ({{column-names}});`

- drop an index:
`drop index [if exists] {{name1}}, {{name2}};`

- drop a table:
`drop table {{table1}}, {{table2}};`
(for really large tables, first truncate)

- update a few fields in a table:
`update {{table}} set {{column1}} = {{expression1}}, {{column2}} = {{expression2}} [where {{condition}}];`

- select from sub-table:
`select {{...}} from (select {{...}}) [t where t.{{condition}}];`

- empty a table:
`delete from {{table}};`
or better performance:
`truncate {{table1}}, {{table2}};`

- count the number of distinct values in a column:
`select count(distinct {{column}}) from {{table}};`

- produce an histogram on some column:
`select {{col}}, count(*) from {{table}} group by {{col}} order by {{col}};`

- pattern matching:
`{{column}} like '{{pattern}}'`
`% = .*`
`_ = .`

- select rows from table1 not found in table2 (in my limited experience the first 2 are the fastest):
`select {{col}} from {{table1}} t1 where not exists (select from {{table2}} where {{col}} = t1.{{col}});`
`select t1.{{col}} from {{table1}} t1 left join {{table2}} t2 using ({{col}}) where t2.{{col}} is null;`
`select {{col}} from {{table1}} except select {{col}} from {{table2}};`

- inner join:
`select {{...}} from {{table1}}, {{table2}} on {{condition}};`

- return 0 rather than no rows for e.g. max or sum queries:
`coalesce({{sum(column)}}, 0)`

- CTE:
`with {{name1}} as ({{subquery1}}), {{name2}} as ({{subquery2}}) {{main-query}};`
