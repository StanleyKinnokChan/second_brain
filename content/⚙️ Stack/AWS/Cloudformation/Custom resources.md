# Custom resources

- logical resources in a template to create, update, and delete physical resources. However, CFN doesn’t support non-native resources
- Custom resources let CFN integrate with anything it doesn’t yet/ doesn’t natively support
- passes data to something, gets data back from something (eg lambda)

eg put data to bucket after creating stack & delete data from bucket before deleting stack

[[Custom resources/Untitled.png]]

- when the stack will send event to lambda when it is subjected to change, lambda will perform certain actions and send the responseURL back to stack

more details version

[[Custom resources/Untitled 1.png]]
