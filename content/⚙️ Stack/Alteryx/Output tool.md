# Output tool

- “OCDB” and “bulk”

    In Alteryx, OCDB (One Connection Database) and Bulk are two different connection options for output tools.

    OCDB is a type of connection where Alteryx opens a single connection to the database and uses it for all the writes to the database during the workflow. This is useful when you need to write to the database multiple times during the workflow, as it reduces the overhead of opening and closing the connection each time. However, using OCDB can lead to longer runtimes if the workflow is writing large amounts of data, as the single connection may become a bottleneck.

    Bulk, on the other hand, is a type of connection that uses the database's native bulk loading capabilities to load large amounts of data into the database quickly. This can be much faster than using OCDB, especially when dealing with large datasets. However, not all databases support bulk loading, and the specific configuration options for bulk loading can vary between databases. Additionally, using Bulk may require additional setup steps or permissions in the database.

    In summary, OCDB is a good choice for workflows that write to the database multiple times but have relatively small amounts of data, while Bulk is a good choice for workflows that need to write large amounts of data quickly, but may require additional setup or permissions in the database.
