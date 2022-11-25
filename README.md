# OpenSGN-Remastered
This project aims to successfully running Debian Jessie (8.11) on Samsung Galaxy Note 10.1 (2012).  

Your warranty is... still valid? After nearly 11 years? Woah, ok then...  
I am not responsible for bricked devices, dead EMMC's, thermonuclear war, or you getting fired because the alarm app doesn't exist. Please read the readme carefully if you have any concerns about bugs in this project before flashing it. You are choosing to make these modifications, and if you point the finger at me for messing up your device, I will laugh at you.  
Also don't forget to get a full backup and saving it to a safe place (especially efs partitition) as there won't be any single thing left from the past on the device while installing.  

![Desktop](https://user-images.githubusercontent.com/111060829/203374100-654b151b-4764-447f-8a31-0383b0d58579.png)

## Caution
This is an experimental project. Although it could be used in a daily basis, don't expect much. Also don't expect any maintenance as I can't even properly work on my main projects because of school.  

## Requirements
Time  
Brain  
Sanity  
Computer  
Galaxy Note 10.1 (2012)  
SD Card  
ADB
7-Zip

## Stability
#### Working:
Display  
Touchscreen  
Stylus  
3D Acceleration  
Wi-Fi
#### Needs fix:
Bluetooth (Needs to be configured)  
Audio (I think somehow I configured it wrong)  
Video playback (Doesn't work because of audio)  
#### Doesn't work:
Sensors  
Camera	
GPS  
Mobile data / SMS / Calls  

## How-To
#### Preperation:
Confirm that you meet all the requirements  
Download all the files in the repository and put them into same folder  
Open the folder you created in terminal  
Reboot tablet to recovery
#### Push parted and make it executable:
```  
adb push parted /  
adb shell  
chmod +x parted  
```  
#### Run parted and set it up:
```  
./parted /dev/block/mmcblk0  
unit mb  
print  
```  
#### Delete all partitions:
```  
rm 1  
rm 2  
rm [partition_number]  
```  
#### Create new partitions and name them:
```  
mkpart primary 4 20  
mkpart primary 20 36  
mkpart primary 36 15754  
name 1 BOOT  
name 2 RECOVERY  
name 3 SYSTEM  
```  
#### Format the newly created system partition:
```  
mke2fs -T ext4 /dev/block/mmcblk0p3  
```  
#### Install recovery:
Reboot tablet to odin mode  
Flash twrp.tar via odin   
#### Install system:
Plug in your SD Card to your computer  
Extract the TWRP folder inside OpenSGN-Remastered.zip and copy it to your SD Card  
Reboot tablet to recovery  
Plug in your SD card to tablet and restore the backup via TWRP  
#### Install boot:
Reboot tablet to odin mode again  
Flash boot.tar via odin  

#### Done!

## Sources Used
[OpenSGN Guide](https://thermatk.github.io/opensgn-easy/)  
[N8000 Native Linux Guide](https://forum.level1techs.com/t/linux-on-the-samsung-galaxy-tab-10-1-and-you-can-too/114142)  
[N8000 Native Linux Thread](https://forum.xda-developers.com/t/n8000-native-linux-thread.2375942/)  
[Repartitioning Guide](https://forum.xda-developers.com/t/tutorial-how-to-resize-system-partition-on-galaxy-s3-for-larger-gapps.4218903/)  