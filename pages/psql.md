# psql

> PostgreSQL client

- start:
`sudo -iu postgres psql [-d {{db-name}}]`

- run SQL query from terminal:
`psql -c '{{query}}'`

- show all configuration options:
`show all;`

- show all configuration options with more details:
`select * from pg_settings;`

- show the config file path:
`show config_file;`

- show results one cell per row:
`\x on`

- redirect results to file or filter through a pipe:
`\o {{filename (/tmp is a good place to put it)}}`
`\o |{{pipe}}`
off:
`\o`

- show tables:
`\d`

- show table schema:
`\d {{table}}`

- time queries:
`\timing [on|off]`

- add an automatically named primary key constraint on a table:
`alter table {{table}} add primary key ({{col1...}});`

- delete a constraint:
`\d {{table}}`
`alter table {{table}} drop constraint {{constraint-name}};`

- on conflict:
`on conflict ({{column-name}}) {{...}}`
`on conflict on constraint {{constraint-name}} {{...}}`

- show the size of a table in bytes (excluding indexes etc):
`select pg_size_pretty(pg_relation_size('{{table}}'));`

- same, but including indexes etc:
`select pg_size_pretty(pg_total_relation_size('{{table}}'));`

- show the size of the indexes of a table:
`select pg_size_pretty(pg_indexes_size('{{table}}'));`

- create a new table like another one:
`create table {{new}} (like {{old}});`

- show a bytea value (in escape format) as a string:
`encode({{column}}, 'escape')`

- transform the elements of an array into rows:
`unnest({{array}})`

- get the size of an array:
`array_length({{array}}, {{dimension (typ. 1)}})`

- insert into table with a serial (auto-incrementing value):
`insert into {{table}} values ({{...}}, DEFAULT, {{...}});`

- max() but one of the arguments is a regular number, not a column:
`greatest()`

- a date:
`'{{2018-01-01}}'::date`
`TO_TIMESTAMP({{bigint}})`

- generate series of dates:
`generate_series('{{2021-03-15}}', '{{2021-03-15}}'::date + interval '{{2 year}}', '{{1 month}}')`

- create a function:
`CREATE [OR REPLACE] FUNCTION {{update_sig}}({{current_sigs int[], sig int}}) RETURNS {{int[]}}`
`LANGUAGE plpgsql [PARALLEL SAFE]`
`AS`
`$$`
`BEGIN`
`{{current_sigs[sig] = current_sigs[sig] + 1}};`
`RETURN {{current_sigs}};`
`END;`
`$$;`

- show source code of a function:
`\sf {{function-name}}`

- create an aggregate (to be used like e.g. sum()):
`CREATE [OR REPLACE] AGGREGATE {{sig_agg}} ({{int}}) (`
`  SFUNC = {{update_sig}},`
`  STYPE = {{int[]}},`
`  INITCOND = {{'{0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0}'}}`
`  [, PARALLEL = SAFE]`
`);`

- knowing the finite number of possible values for a column, count the number of occurrences of each of them, grouping by some value:
`select {{...}},`
`  sum(({{col}} = {{val1}})::int) as {{v1}},`
`  sum(({{col}} = {{val2}})::int) as {{v2}},`
`  {{...}}`
`  from {{table}}`
`  group by {{value}};`
