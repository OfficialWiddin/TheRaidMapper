# The Raid Mapper  

![Python 2.7](https://img.shields.io/badge/python-2.7-blue.svg)

The Raid Mapper is a Raid scanner for Pokemon GO, based on Android devices and OCR.  

<img src="https://raw.githubusercontent.com/Grennith/TheRaidMapper/master/examples/example_map.PNG" width="500" height="500">

## Information
*  [Discord](https://discord.gg/MC3vAH9) - For general support  
*  [Github Issues](https://github.com/Grennith/TheRaidMapper/issues) - For reporting bugs (not for support!)  

## Requirements  
* [PogoAssets](https://github.com/ZeChrales/PogoAssets)  
* Google or PTC account with minimum level 5 and no Raid-bosses in the dex  
* Mobile with Android 8.0 (API 26) or higher
* Root privileges [Magisk](https://forum.xda-developers.com/apps/magisk/official-magisk-v7-universal-systemless-t3473445) and [Terminal APP Systemizer](https://forum.xda-developers.com/apps/magisk/module-terminal-app-systemizer-ui-t3585851)  
*  [Droid VNC Server](https://github.com/Grennith/TheRaidMapper/blob/master/APKs/VNC_app.apk) and [Remote GPS Controller](https://github.com/Grennith/TheRaidMapper/blob/master/APKs/RemoteGpsController.apk)  

## Current limitations
* The only supported aspect ratio is 16:9. If you have a softkey bar, disable it for PoGO.  
* It takes time to load when you teleport between different locations. So faster phones may handle the loading better. We are testing on low end specs like [Redmi 5A](https://www.mi.com/in/redmi-5a/) for $75. A parameter to adjust the delays in between teleports and screenshots will most likely be added.   
* Sometimes the Raids won't get reported to the DB and we are in the process of debugging it. A potential help is removing the files inside the hash-folder.  
* The Droid VNC Server can have hick-ups. The VNC app which is based on [droidVNC](https://github.com/oNaiPs/droidVncServer).
> The app is not stable. We had it running for weeks and it would just give up for a whole day. We are planning on releasing our very own app. As Stupid as it may sound, an apparent workaround might be: Start droidVNC -> Start Server -> Switch out of the app and go to System Settings -> Apps -> droidVNC -> Force stop. The server itself should continue running.

## Installation
### Prerequisites - Computer
Install `Python 2.7` according to docs for your platform.  

Once Python is installed, ensure that `pip` and `Python` is installed correctly by running:  
* `python --version` - should return `2.7.X`  
* `pip --version` - If it returns a version, it is working. If not, [visit here](https://packaging.python.org/tutorials/installing-packages/#ensure-you-can-run-pip-from-the-command-line)  


To run a copy from the latest develop branch in git you can clone the repository:  
`git clone https://github.com/Grennith/TheRaidMapper.git`  

Make sure you're in the directory of TheRaidMapper and run:  
`pip install -r requirements.txt`

*Depending on your OS, you may need to install the following:*
* Ubuntu/Debian
```bash
sudo apt update
sudo apt install tesseract-ocr python-opencv
```
* MacOS (Using Brew ([How to Install Brew](https://brew.sh/)))
```bash
brew install imagemagick
brew install tesseract --all-languages
```
* Windows
```bash
// TODO
```
### Prerequisites - Mobile
1. Install [Magisk](https://forum.xda-developers.com/apps/magisk/official-magisk-v7-universal-systemless-t3473445) and [Terminal App Systemizer](https://forum.xda-developers.com/apps/magisk/module-terminal-app-systemizer-ui-t3585851) by flashing ([App Installs/ROM Feature Installs via Flashing](https://forum.xda-developers.com/wiki/Flashing_Guide_-_Android)).  

2. Install [VNC_app.apk](https://github.com/Grennith/TheRaidMapper/blob/master/APKs/VNC_app.apk) & [RemoteGpsController.apk](https://github.com/Grennith/TheRaidMapper/blob/master/APKs/RemoteGpsController.apk) located in the `APKs` github folder.

3. Install [Terminal Emulator](https://play.google.com/store/apps/details?id=jackpal.androidterm&hl=en) from Google Play and run:
```
su
systemize
1
<insert number of RemoteGpsController>
2
0
0
reboot
```

### MySQL - Database  
You will need a MySQL server installed:  
* (Tutorial from RocketMap) [Installing MySQL](https://rocketmap.readthedocs.io/en/develop/basic-install/mysql.html) 

### Configuration
1. Rename `config.ini.example` to `config.ini` and fill out:  
    - MySQL Settings  
    - Device Specifics  
    - Path Settings (pogoasset only)  
    - Timezone Settings  
    - Coords CSV (Create a "coords.csv" file and set `file: coords.csv`)  

</br>

2) We need gym images and there are two solutions:  
    - If you have a RocketMap database with old gym-details, run `downloadfortimg.py`  
    - Or, grab the images from [Ingress Intel Map](https://www.ingress.com/intel)  

(The images should be located in `gym_img` folder)

</br> 

3) We also need gym locations and there are two solutions:
    - If you have a RocketMap database with old gym-details, run `downloadDBCords.py`  
    - Or, grab the locations from [Ingress Intel Map](https://www.ingress.com/intel)  

(The coords should be located in `coords.csv` if you followed the last step in 1.)

</br>

4) Fill out the rest of the `config.ini`, the important parts are:  
    - VNC Settings
    - Telnet Settings (RemoteGpsController)

### Running
1. Mobile - Start the Droid VNC Server.  
*(Start droidVNC -> Start Server -> Switch out of the app and go to System Settings -> Apps -> droidVNC -> Force stop. The server itself should continue running.)*

</br>

2. Mobile - Start Remote GPS Controller.

</br>

3. Mobile - Start Pokémon GO

</br>

4. PC - Make sure you're in the directory of TheRaidMapper and run `python startWalker.py`

<br>

**WE DO NOT GUARANTEE IT WILL BE RUNNING PERFECTLY FINE, AS THE PROJECT IS IN ONGOING DEVELOPMENT**

## TODO
* Write tests  
* Finding replacement for Droid VNC Server  
* Improve scans  
* Improve error handling  
* Support more/all resolutions  

## Updating the application
Make sure you're in the directory of TheRaidMapper and run:  
```
git pull
pip install -r requirements.txt 
```

License
----

See [LICENSE - GNU GENERAL PUBLIC LICENSE](https://github.com/Grennith/TheRaidMapper/blob/master/LICENSE).
