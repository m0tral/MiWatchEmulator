# MiWatchEmulator
## Description
Xiaomi Watch Windows based emulator, for watchfaces and apps

This emulator allows test and debug as ready watchfaces as ready app.  
All is prepared, so just unpack and run.  
Tested under Windows 10 and 11.  

Ready sizes are:
- Redmi Watch 4
- Redmi WAtch 5
- Xiaomi Watch S3 (S1, S2, S4 compatible)

Will add Mb8Pro/Mb9Pro soon

![emulator RedmiWatch4](/img/emulator_rw4.png)

## Steps how to install a watchface manually

To interact with emulator system inside you should use adb command, provided in pack

### 1. Validate a list of installed watchfaces
```batchfile
adb shell ls -l /data/app/watchface/market
```

### 2. Create a dir for new watchface
```shell
adb shell mkdir /data/app/watchface/market/362700xxx
```
where should be ID of watchface,
make it unique to avoid conflicts

### 3. Upload a watchface file
```ssh
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

## Additional commands
### Set a desired system language
```
adb shell setprop persist.locale ru_RU
adb shell setprop persist.locale es_ES
```
the watch emulator supports 30 locales

### Set a desired date and time
```
adb shell reboot
```
### Take a generated watchface preview from emulator
```ssh
adb pull /data/app/watchface/market/362700xxx/preview.bin d:\faces\face_preview.bin
```
### Take a screenshot
```
adb shell dd if=/dev/fb0 of=/data/fb_dump.bin
adb pull /data/fb_dump.bin d:\faces\screenshot.bin
```
