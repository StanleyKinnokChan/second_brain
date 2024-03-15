# Streams & Lambda Triggers

**Stream**

[[Streams & Lambda Triggers/Untitled.png]]

<aside>
💡 A *DynamoDB stream* is an time-ordered flow of information about changes to items in a DynamoDB table. When you enable a stream on a table, DynamoDB captures information about every modification to data items in the table.

It writes a stream record with the primary key attributes of the items that were modified. A *stream record* contains information about a data modification to a single item in a DynamoDB table.

</aside>

- 24-hr rolling window
- has to be enabled on a per table basis
- different **view types** can influence what is in the stream

**Trigger**

- item changes generate an **event**, which contained the changed data
- then **an action** is taken using that data
- AWS = **streams + lambda**
- reporting, analytics, aggregation, messaging, notification

**Architecture**

[[Streams & Lambda Triggers/Untitled 1.png]]
