# Quick create scripts
```CQL
use test_table_space;
select * from test_table;

insert into test_table(ssn, first_name, last_name) values (1, '1-first', '1-last');
insert into test_table(ssn, first_name, last_name) values (2, '2-first', '2-last');
insert into test_table(ssn, first_name, last_name) values (3, '3-first', '3-last');

alter table test_table add new_column boolean; --Will default to false
```
# Concurrency features
Each column has a timestamp. When Cassandra has to reconcile data, the last write wins. You can set a writetime on a column when you update it, however if it's earlier than the column's current writetime the update is *ignored*.
# Caching features
Each column has a TTL value - it's `null` by default, i.e. - the value never expires. There is no way to set the TTL value for an entire row. We have to set every non-primary key value to do so while specifying TTL on an update column.
