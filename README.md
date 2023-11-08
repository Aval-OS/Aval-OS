# Aval-OS
Main repository for the Aval Operating System, a security focused microkernel architecture OS for the future.

Every object on the system is locked with a 4-bit tag via MTE, and follows typical Rust borrowing & ownership semantics 
When a process needs access to an object:
1) Process will request to borrow a capability to the object and create a handle.
2) The operating system will return a fat pointer to the object with the matching tag.
3) The Process will use the Handle for the purposes it needs.
4) When the capabilty is borrowed or returned to the OS, the tag changes.

```rs
let handle: Capability = borrow("object"); //returns capability w/ tag
handle.action();
handle2 = handle; // capability to object is moved, key is changed.

handle2.action(); // This is fine
handle.action(); // This will trigger a tag fault.

// Capability is returned to the operating system at the end of it's life, changing the key.
```
