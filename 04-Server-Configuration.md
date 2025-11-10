# Step 4: Configuring PalWorldSettings.ini

Your server is running with default settings. Now, let's customize the game rules, name, and password.

## 1. Stop the Server

You must stop the server before editing its configuration.
```bash
systemctl stop palworld
```

## 2. Prepare the Configuration File

By default, the settings file is blank. We must copy the default template to create the file we can edit.

1.  Switch to your `steam` user:
    ```bash
    su - steam
    ```
2.  Navigate to the server's root directory:
    ```bash
    cd ~/palworld
    ```
3.  Copy the default settings file to the correct location:
    ```bash
    cp DefaultPalWorldSettings.ini Pal/Saved/Config/LinuxServer/PalWorldSettings.ini
    ```

## 3. Edit the Settings

1.  Open the newly created settings file in a text editor:
    ```bash
    nano Pal/Saved/Config/LinuxServer/PalWorldSettings.ini
    ```
2.  You will see a file with two lines. **All settings must be placed on the second line**, inside the `(...)` and separated by commas.

    **Example Structure:**
    ```ini
    [/Script/Pal.PalGameWorldSettings]
    OptionSettings=(Setting1=Value,Setting2=Value,Setting3="TextValue",...)
    ```

## 4. Common Settings to Change

Find these settings within the `OptionSettings=(...)` line and change their values.

| Setting | What it Does | Default |
| :--- | :--- | :--- |
| `ServerName` | Your server's name in the list. | `"Default Palworld Server"` |
| `ServerPassword` | A password to join your server. | `""` (empty) |
| `AdminPassword` | Password to get admin rights. | `""` (empty) |
| `ServerPlayerMaxNum` | Max players on the server. | `32` |
| `ExpRate` | Experience gain multiplier. | `1.000000` |
| `PalCaptureRate` | How easy it is to catch Pals. | `1.000000` |
| `PalEggDefaultHatchingTime` | Time in hours to hatch an egg. (Lower = faster) | `72.000000` |
| `DayTimeSpeedRate` | How fast the day passes. | `1.000000` |
| `NightTimeSpeedRate`| How fast the night passes. | `1.000000` |
| `DeathPenalty` | What you drop on death (`None`, `Item`, `ItemAndEquipment`, `All`).| `All` |

**Important:** Text values (like server name) **must** be enclosed in quotes (`"`).

## 5. Restart the Server

1.  Save and exit the text editor (`Ctrl+O`, `Enter`, `Ctrl+X`).
2.  Return to the `root` user:
    ```bash
    exit
    ```
3.  Start the server to apply your new settings:
    ```bash
    systemctl start palworld
    ```

Your server is now running with your custom settings.

---
**➡️ Next Step: [Step 5: Server Maintenance](./05-Maintenance.md)**
