---
title: cfn-hup
tags:
  - aws
---

# cfn-hup

- [[cfn-init]] only **run once** as part of bootstrapping (user data)
- ..if cloudformation::init is updated, **it isn’t rerun**

    <aside>
    💡 **cfn-hup helper** is a daemon (background process) that detects changes in resource metadata and runs user-specified actions when a change is detected. This allows you to make configuration updates on your running Amazon EC2 instances through the `UpdateStack` API action.

    </aside>


[[cfn-hup/Untitled.png]]
