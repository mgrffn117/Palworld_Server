# Step 3: `systemd` Service Setup (Continuous Operation)

This is the most important step for making your server run 24/7. We will create a `systemd` service to manage the server process.

## 1. Return to `root`

You should still be in the `steam` user's session. Type `exit` to return to the `root` user.
```bash
exit
```

## 2. Create the Service File

1.  Use a text editor (like `nano`) to create a new service file:
    ```bash
    nano /etc/systemd/system/palworld.service
    ```

2.  Paste the following configuration into the editor. This file tells `systemd`:
    * Who to run the server as (`User=steam`).
    * Where the server files are (`WorkingDirectory`).
    * What command to run (`ExecStart`).
    * To always restart it if it fails (`Restart=always`).

    ```ini
    [Unit]
    Description=Palworld Dedicated Server
    Wants=network-online.target
    After=network-online.target
    
    [Service]
    User=steam
    Group=steam
    WorkingDirectory=/home/steam/palworld
    ExecStart=/home/steam/palworld/PalServer.sh -useperfthreads -NoAsyncLoadingThread -UseMultithreadForDS
    Restart=always
    RestartSec=5
    LimitNOFILE=100000
    
    [Install]
    WantedBy=multi-user.target
    ```

3.  Save and exit the file. (In `nano`, press `Ctrl+O`, `Enter`, then `Ctrl+X`).

## 3. Enable and Start the Service

1.  Reload `systemd` to make it read your new file:
    ```bash
    systemctl daemon-reload
    ```
2.  Enable the service (this makes it start automatically when the LXC boots):
    ```bash
    systemctl enable palworld.service
    ```
3.  Start the server for the first time:
    ```bash
    systemctl start palworld.service
    ```

## 4. Verify It's Running

You can check the status of your server at any time with:
```bash
systemctl status palworld.service
```
If you see `active (running)` in green, your server is live!

## 5. Port Forwarding (Final Step)

Your server is running inside the LXC, but the outside world can't connect.

1.  Log in to your **home router's admin page**.
2.  Find the **"Port Forwarding"** section.
3.  Create a new rule:
    * **Port:** `8211`
    * **Protocol:** `UDP`
    * **Destination/Internal IP:** The static IP you set for your LXC (e.g., `192.168.1.50`).

Your friends can now connect to your server using your **public IP address**.

---
**➡️ Next Step: [Step 4: Server Configuration](./04-Server-Configuration.md)**
