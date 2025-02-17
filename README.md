# MiWatchEmulator
## Description
Xiaomi Watch Windows based emulator, for watchfaces and apps

This emulator allows test and debug as ready watchfaces as ready app.  
All is prepared, so just unpack and run.  
Tested under Windows 10 and 11.  

![emulator RedmiWatch4](/img/emulator_rw4.png)

## Steps how to install a watchface manually

To interact with emulator system inside you should use adb command, provided in pack

### 1. Validate a list of installed watchfaces
```
adb shell ls -l /data/app/watchface/market
```

### 2. Create a dir for new watchface
```
adb shell mkdir /data/app/watchface/market/362700xxx
```
where should be ID of watchface,
make it unique to avoid conflicts

### 3. Upload a watchface file
```
adb push d:\faces\resource.bin /data/app/watchface/market/362700xxx
```
you have to change it in watchface file header too, in any hex editor ID,  
or take it from admin panel with ready ID

### 4. Delete a watchfaces description
```
adb shell rm /data/app/watchface/watchface_list.json
```
### 5. Reboot watch to force create a new watchfaces list
```
adb shell reboot
```
