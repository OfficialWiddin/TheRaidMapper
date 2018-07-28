# The Raid Mapper

The Raid Mapper is a raid scanner for Pokemon GO based on Android devices.
It consists of two parts:
1) OCR
2) Scan

The result is a map (RocketMap to be precise) filled with raid bosses or eggs with their time and tier.

Example screen
![Map Example](examples/example_map.png?raw=true "Map Example")

# Requirements
#### General
1) A computer (RaspberryPI likely is sufficient as well)
2) A RM DB with gymdetails for the gyms you intend to scan (you can download the gym images with those details...). Alternative: Get the ingress images of the gyms you want to scan...

#### OCR
The OCR part requires screenshots to come in. If you already have RDRM (Real Device Raid Mapper) running, you could use the OCR part to send information to RM.
1) [PoGoAssets](https://github.com/ZeChrales/PogoAssets)
2) Mons need to not have been seen. Get yourself a fresh account without even T1 mons

#### Scan
1) Android 8.0 (API 26) or higher
2) Root privileges (Magisk) and flashing [Terminal APP Systemizer](https://forum.xda-developers.com/apps/magisk/module-terminal-app-systemizer-ui-t3585851)
3) VNC app and RemoteGpsController.apk (the latter requires System privileges)

We provide a VNC app which is based on [droidVNC](https://github.com/oNaiPs/droidVncServer).
> The app is not stable. We had it running for weeks and it would just give up for a whole day. We are planning on releasing our very own app.
As Stupid as it may sound, an apparent workaround might be:
Start droidVNC, start Server, switch out of app and go to System Settings -> Apps -> droidVNC -> Force stop. The server itself should continue running.

### Current limitations
1) For the moment only 9:16 aspect ratio phones are supported. If you have a softkey bar, disable it for PoGo.
2) VNC app can have hick-ups....
3) Teleporting from location to location takes the game time to load images. Faster phones may handle it better. We are testing on low end specs (Redmi 5A for $75). We will likely add a parameter to set the delays in between teleports and screenshots.
4) Sometimes mons do not get reported to the DB. We are in the process of debugging. It can help to remove the files in the hash-folder however.

# Installation
Install Python 2.7 according to docs for your platform.

Once Python is installed ensure that `pip` is installed by running
`pip --version` if it returns a version it is setup if not [visit here](https://packaging.python.org/tutorials/installing-packages/#ensure-you-can-run-pip-from-the-command-line)

Once `pip` is installed run

`pip install -r requirements.txt`

*Depending on your OS, you may need to install the following*
#### For Ubuntu/Debian
```bash
sudo apt update
sudo apt install tesseract-ocr python-opencv
```
#### For MacOS (Using Brew ([How to Install Brew](https://brew.sh/)))
```bash
brew install imagemagick
brew install tesseract --all-languages
```
#### For Windows
```bash
TBC
```

# WE DO NOT GUARANTEE FOR THE ENTIRE THING TO BE RUNNING PERFECTLY FINE

### Todos

 - Write tests
 - Write VNC app
 - Improve scans
 - Improve error handling
 - Support more/all resolutions

# Need Help...Join The Discord
For minor help, reporting bugs and reporting resolutions (instructions on how will be given in due course)
[Join the discord server](https://discord.gg/MC3vAH9)


License
----

GNU GPL
