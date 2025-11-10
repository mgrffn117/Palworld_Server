# Step 2: Server Installation (Inside LXC)

Now we will log into the container and install all the necessary software.

## 1. Log In and Update

1.  Start your new LXC container from the Proxmox UI.
2.  Open the **"Console"**.
3.  Log in as `root` with the password you set during creation.
4.  Update the package lists and upgrade all software:
    ```bash
    apt update && apt upgrade -y
    ```

## 2. Install Dependencies

SteamCMD is a 32-bit application, so we must enable the i386 architecture and install its dependencies.

```bash
# Enable 32-bit architecture
dpkg --add-architecture i386

# Update package lists
apt update

# Install dependencies (lib32gcc-s1 is the most important one)
apt install -y curl lib32gcc-s1
```

## 3. Create a Non-Root User

It is a security risk to run game servers as the `root` user. We will create a dedicated user named `steam`.

```bash
# Create the 'steam' user, create their home directory, and set their shell
useradd -m -s /bin/bash steam

# Switch to the new user's session
su - steam
```
**You will now be operating as the `steam` user.**

## 4. Install SteamCMD

1.  As the `steam` user, create a directory for SteamCMD and enter it:
    ```bash
    mkdir ~/steamcmd && cd ~/steamcmd
    ```
2.  Download and extract SteamCMD:
    ```bash
    curl -sqL "[https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz](https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz)" | tar zxvf -
    ```

## 5. Install the Palworld Server

1.  Now, we'll run a single command to download/update the Palworld Dedicated Server (App ID `2394010`) into a new `~/palworld` directory.
    ```bash
    ./steamcmd.sh +force_install_dir ~/palworld +login anonymous +app_update 2394010 +quit
    ```

2.  **Troubleshooting:** If the command hangs on **"Waiting for user info..."**:
    * Press `Ctrl+C` to cancel.
    * Run SteamCMD interactively once to let it self-update:
        ```bash
        ./steamcmd.sh
        ```
    * At the `Steam>` prompt, type `exit` and press Enter.
    * Re-run the full download command from step 1.

Once this is complete, all server files will be in `/home/steam/palworld`.

---
**➡️ Next Step: [Step 3: `systemd` Service Setup](./03-Systemd-Service.md)**
