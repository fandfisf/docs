# Concurrency features
Each column has a timestamp. When Cassandra has to reconcile data, the last write wins. You can set a writetime on a column when you update it, however if it's earlier than the column's current writetime the update is *ignored*.
