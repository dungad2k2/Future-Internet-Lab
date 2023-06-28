# **Nova** (Compute Service):
## Introduction about Nova:
- OpenStack Compute is used to host and manage cloud computing systems and is a major part of an Infrastructure-as-a-Service(IaaS) system.
- OpenStack Compute interacts with OpenStack Identity for authentication. OpenStack Image service for disk and server images and OpenStack Dashboard for the user and administrative interface.
## Components of OpenStack Compute:
- `nova-api` service : accepts and responds to end user compute API calls. This service supports the OpenStack Compute API, the Amazon EC2 API and a special Admin API for special users to perform administrative actions. It enforces some policies and initiates most orchestration activities, such as running an instance. 
> orchestration activities: hoạt động điều phối. 
- `nova-api-metadata` service: accecpts [metadata](https://docs.openstack.org/2023.1/admin/#metadata-service) requests from instances and generally used when you run in multi-host mode with `nova network` installations.
- `nova-compute` service: a daemon that creates and terminates virtual machine instances through hypervisor APIs. It's complex but basically, the daemon accepts actions from the queue and performs a series of system commands such as launching a KVM instance and updating its state in the database. For examples:
  - XenAPI for XenServer/XCP.
  - libvirt for KVM or QEMU.
  - VMwareAPI for VMware.
- `nova-placement-api` service: Tracks the inventory and usage of each provider.
- `nova-scheduler` service: Takes a virtual machine instance request from the queue and determines on which compute server host it runs.
- `nova-conductor` module: Between `nova-compute` service and the database interactions. It eliminates direct accesses to the cloud database made by the `nova-compute` service.
- `nova-cert` module: A server daemon that serves the Nova Cert service for X509 certificates. Used to generate certificates for 'euca-bundle-image' -> Only needed for the EC2 API.
- `nova-consoleauth` daemon: Authorizes tokens for users that console proxies provide.
- `nova-novncproxy` daemon: Provide a proxy for accessing running instances through a VNC connection. Supports browser-based novnc clients.
- `nova-xvpvncproxy` daemon: Provide a proxy for accessing running instances through a VNC connection. Supports an OpenStack-specific Java client.
- `nova-spicehtml5proxy` daemon: Provide a proxy for  accessing running instances through a SPICE connection. Supports brower-based HTML5 client.
### The queue: 
- Is a central hub for passing messages between daemons. Usually implemented with RabbitMQ, also can be implemented with another AMQP message queue, such as ZeroMQ.
### SQL database:
- Stores most build-time and run-time states for a cloud infrastructure.
- Supports any database that SQLAlchemy supports (SQlite3, MySQL, MariaDB,...).