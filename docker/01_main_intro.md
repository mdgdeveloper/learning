# Documentation
[Docker Main Documentation](https://docs.docker.com/)

# Namespaces Isolation

Linux namespaces provide isolation based on:

- PID: Containers with its own Process ID
- MNT: Mount and unmount directories without affecting other namespaces.
- NET: Containers have their own network stack.
- IPC: Isolated interprocess communication mechanisms such as message queues.
- User: Isolated view of users on the system.
- UTC: Set hostname and domain name per container.