# Step 5: Server Maintenance

Here are the common commands you'll need to manage and update your Palworld server.

## 1. Managing the Server Process

All of these commands must be run as the `root` user in your LXC console.

### Check Server Status
This is the most useful command. It shows if the server is `active (running)` and displays the latest console log entries.
```bash
systemctl status palworld
```
(Press `q` to exit the status log).

### Start the Server
If the server is stopped, this will start it.
```bash
systemctl start palworld
```

### Stop the Server
This gracefully stops the server.
```bash
systemctl stop palworld
```

### Restart the Server
This is a quick way to stop and then start the server, which is useful for applying config changes.
```bash
systemctl restart palworld
```

## 2. How to Update Your Palworld Server

When the game receives an update, you will need to update your server files.

1.  **Stop the server** (as `root`):
    ```bash
    systemctl stop palworld
    ```
2.  **Switch to the `steam` user**:
    ```bash
    su - steam
    ```
3.  **Run the update command** (this is the same command we used to install):
    ```bash
    ~/steamcmd/steamcmd.sh +force_install_dir ~/palworld +login anonymous +app_update 2394010 +quit
    ```
    SteamCMD will only download the new/changed files.
4.  **Return to the `root` user**:
    ```bash
    exit
    ```
5.  **Start the server** (as `root`):
    ```bash
    systemctl start palworld
    ```

Your server is now updated and running.
