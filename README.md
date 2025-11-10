# Palworld Dedicated Server on Proxmox LXC

This guide provides a complete, step-by-step process for setting up a dedicated Palworld server inside a Proxmox LXC (Linux Container). This method is extremely resource-efficient, using significantly less RAM and CPU than a full Virtual Machine.

The server is configured to run as a `systemd` service, meaning it will automatically start when the container boots and automatically restart if it crashes.

## Prerequisites

* A working Proxmox VE host.
* An Ubuntu 22.04 (or newer) LXC template downloaded on your Proxmox host.
* Basic knowledge of the Linux command line.
* Access to your home router's admin page for port forwarding.

## Guide Contents

This guide is broken down into logical steps. Follow them in order.

1.  [**Step 1: Proxmox LXC Creation**](./01-LXC-Creation.md)
    * How to create and configure the base LXC container in the Proxmox UI.

2.  [**Step 2: Server Installation (Inside LXC)**](./02-Server-Install.md)
    * Installing dependencies, creating a non-root user, and installing SteamCMD and the Palworld server files.

3.  [**Step 3: `systemd` Service Setup**](./03-Systemd-Service.md)
    * Creating the service file to ensure the server runs continuously and restarts on crashes.

4.  [**Step 4: Server Configuration**](./04-Server-Configuration.md)
    * How to find, edit, and configure your server's `PalWorldSettings.ini` to change game rules, server name, and password.

5.  [**Step 5: Server Maintenance**](./05-Maintenance.md)
    * Common commands for starting, stopping, and updating your server.
