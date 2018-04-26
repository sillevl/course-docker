# What is Docker?

![Docker logo](.gitbook/assets/docker-logo.jpg)

Docker is a tool for running software in an isolated environment.

It offers advantages similar to running applications in virtual machines.

1. Same environment
2. Sandboxed projects \(security and conflicting dependencies\)
3. It just works \(all dependencies are available inside the container\)

All advantages of a virtual machine without the overhead of a virtual machine:

Containers all use the same kernel of the host machine.

Special features of the Linux system to create isolated environment. Docker is a bundle of existing proven linux tools \(chroot, cgroups, ...\).

Containers are a compromise: separation and sandboxing are not strict, but its enough

Containers start up in seconds. Use less resources, and less memory.

