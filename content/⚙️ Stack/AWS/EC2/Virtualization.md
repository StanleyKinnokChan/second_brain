# Virtualization

**Normally without virtualization**

- application layer make user calls to OS
- OS make privileged calls to hardware

[[Virtualization/Untitled.png]]

**Emulated Virtualization**

- host OS/hypervisor still run on the hardware, allocated the resource to guest OS
- guest OS were wrapped a container called virtual machine that can make privileged call and interact with the hardware
- binary translation make these calls into hypervisor call as if host OS calls them
- tend to be slow because of the binary translation

    [[Virtualization/Untitled 1.png]]


**Para-virtualization**

- only works on a small subset of OS, which can be modified to make guest OS’s privileged call into user call calls the hypervisor (hypercalls)
- still trying to trick the hardware

[[Virtualization/Untitled 2.png]]

**Hardware assisted virtualization**

- hardware itself has become virtualization aware
- CPU contains specific instruction and capabilities and understand it’s performing virtualization
- the calls are redirected to the hypervisor by the hardware and hypervisor handle how’re they executed
- SR-IOV procedure makes devices into multiple logical mini devices allowing the VM to use

[[Virtualization/Untitled 3.png]]
