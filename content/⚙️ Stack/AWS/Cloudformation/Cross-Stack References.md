# Cross-Stack References

- it allow the reuse of existing resource created by other stacks
    - nested stack just for reusing the template!!
- outputs are normally **not visible** from other stacks
- Nested stacks can reference them
- outputs can be **exported**..making them **visible** from other stacks
- **exports must have a unique name in the regions**
- **Fn::ImportValue** can be used for referencing the resource of which stack has ‘export’ in the output

[[Cross-Stack References/Untitled.png]]
