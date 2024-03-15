# DependsOn

- **CF does things in parallel** (create, update & delete) and tries to determine a dependency order (VPC ⇒ SUBNET ⇒ EC2) by references/ functions, but sometimes it doesn’t work when the structure is complex
- DependsON lets you **explicitly** define these resources, complete one before another

[[DependsOn/Untitled.png]]
