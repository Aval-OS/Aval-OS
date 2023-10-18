# Aval-OS
Main repository for the Aval Operating System.

An object-capability model operating system that runs all applications with their own kernel.

## How it will work

The seL4 microkernel will run as a hypervisor, and will virtualize all applications on the system in containers.
Each container will be bundled with it's own linux kernel and dependencies.
Each kernel will only be granted the resources given to it by the seL4 hypervisor, ommitting the need for a security module as the kernel will not be able to serve resources not granted to the container.
