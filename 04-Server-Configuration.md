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
## 4.5 Here is the full string of all options KEEP IT ALL ON ONE LINE!
OptionSettings=(Difficulty=None,RandomizerType=None,RandomizerSeed="",bIsRandomizerPalLevelRandom=False,DayTimeSpeedRate=1.000000,NightTimeSpeedRate=1.000000,ExpRate=1.000000,PalCaptureRate=1.000000,PalSpawnNumRate=3.000000,PalDamageRateAttack=1.000000,PalDamageRateDefense=1.000000,PlayerDamageRateAttack=1.000000,PlayerDamageRateDefense=1.000000,PlayerStomachDecreaceRate=.5,PlayerStaminaDecreaceRate=.5,PlayerAutoHPRegeneRate=2.000000,PlayerAutoHpRegeneRateInSleep=5.000000,PalStomachDecreaceRate=1.000000,PalStaminaDecreaceRate=1.000000,PalAutoHPRegeneRate=1.5,PalAutoHpRegeneRateInSleep=5.000000,BuildObjectHpRate=1.000000,BuildObjectDamageRate=1.000000,BuildObjectDeteriorationDamageRate=1.000000,CollectionDropRate=1.5,CollectionObjectHpRate=1.000000,CollectionObjectRespawnSpeedRate=1.000000,EnemyDropItemRate=1.000000,DeathPenalty=none,bEnablePlayerToPlayerDamage=False,bEnableFriendlyFire=False,bEnableInvaderEnemy=True,bActiveUNKO=False,bEnableAimAssistPad=True,bEnableAimAssistKeyboard=False,DropItemMaxNum=3000,DropItemMaxNum_UNKO=100,BaseCampMaxNum=128,BaseCampWorkerMaxNum=20,DropItemAliveMaxHours=1.000000,bAutoResetGuildNoOnlinePlayers=False,AutoResetGuildTimeNoOnlinePlayers=72.000000,GuildPlayerMaxNum=20,BaseCampMaxNumInGuild=4,PalEggDefaultHatchingTime=0.000000,WorkSpeedRate=1.000000,AutoSaveSpan=30.000000,bIsMultiplay=False,bIsPvP=False,bHardcore=False,bPalLost=False,bCharacterRecreateInHardcore=False,bCanPickupOtherGuildDeathPenaltyDrop=False,bEnableNonLoginPenalty=True,bEnableFastTravel=True,bIsStartLocationSelectByMap=True,bExistPlayerAfterLogout=False,bEnableDefenseOtherGuildPlayer=False,bInvisibleOtherGuildBaseCampAreaFX=False,bBuildAreaLimit=False,ItemWeightRate=.5,CoopPlayerMaxNum=4,ServerPlayerMaxNum=32,ServerName="Gryphon's Isles",ServerDescription="",AdminPassword="",ServerPassword="",PublicPort=8211,PublicIP="",RCONEnabled=False,RCONPort=25575,Region="",bUseAuth=True,BanListURL="https://api.palworldgame.com/api/banlist.txt",RESTAPIEnabled=False,RESTAPIPort=8212,bShowPlayerList=False,ChatPostLimitPerMinute=30,CrossplayPlatforms=(Steam,Xbox,PS5,Mac),bIsUseBackupSaveData=True,LogFormatType=Text,bIsShowJoinLeftMessage=True,SupplyDropSpan=180,EnablePredatorBossPal=True,MaxBuildingLimitNum=0,ServerReplicatePawnCullDistance=15000.000000,bAllowGlobalPalboxExport=True,bAllowGlobalPalboxImport=True,EquipmentDurabilityDamageRate=0,ItemContainerForceMarkDirtyInterval=1.000000,ItemCorruptionMultiplier=1.000000)

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
