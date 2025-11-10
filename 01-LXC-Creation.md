# Step 1: Proxmox LXC Creation

This section covers the creation of the LXC container on your Proxmox host.

## 1. Download the Template

1.  In your Proxmox web UI, select your `local` storage (or other template storage).
2.  Go to **CT Templates** -> **Templates**.
3.  Search for `ubuntu-22.04-standard` (or a newer LTS) and click **Download**.

## 2. Create the Container (CT)

1.  Click the blue **"Create CT"** button in the top-right of the Proxmox UI.
2.  Fill out the tabs with the following settings:
    * **General:**
        * **Hostname:** `palworld-server` (or your preferred name)
        * **Password:** Set a strong root password for the container.
    * **Template:**
        * **Template:** Select the `ubuntu-22.04` template you downloaded.
    * **Storage:**
        * **Disk size:** 20GB (This is a safe starting point. You can resize it later).
    * **CPU:**
        * **Cores:** 2 or 4 (Palworld can be CPU-intensive).
    * **Memory:**
        * **Memory:** 8192 MB (8GB) is a recommended *minimum*. 16384 (16GB) is safer for more players.
    * **Network:**
        * **IPv4:** `Static`
        * **IPv4/CIDR:** Assign a static IP from your network (e.g., `192.168.1.50/24`).
        * **Gateway:** Set your router's IP (e.g., `192.168.1.1`).
    * **DNS:**
        * Use your router's IP or a public DNS like `1.1.1.1`.

3.  Confirm and create the container.

## 3. Set to Start at Boot

1.  Select your new `palworld-server` LXC in the Proxmox UI.
2.  Go to the **Options** tab.
3.  Find **"Start at boot"**, double-click it, and check the **"Yes"** box.

This ensures that if your Proxmox host reboots, your server container will start automatically.

---
**➡️ Next Step: [Step 2: Server Installation](./02-Server-Install.md)**
