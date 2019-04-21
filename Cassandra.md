# Concurrency features
Each column has a timestamp. When Cassandra has to reconcile data, the last write wins. You can set a writetime on a column when you update it, however if it's earlier than the column's current writetime the update is *ignored*.
# Caching features
Each column has a TTL value - it's `null` by default, i.e. - the value never expires. There is no way to set the TTL value for an entire row. We have to set every non-primary key value to do so while specifying TTL on an update column.
