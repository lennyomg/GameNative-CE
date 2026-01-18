# GameNative CE and PICO-8

**Download PICO-8**

[Buy PICO-8](https://www.lexaloffle.com/pico-8.php) and download the Windows version. Create a new folder `Pico8` (or another name) in the phone storage. Unzip the PICO-8 files into the `Pico8` folder. Create a new subfolder `home` inside the `Pico8` folder. The home folder must be named `home`. It is where PICO-8 stores downloads and carts.

It should look like this:
```
PHONE/
   Documents/
   Download/
   Pico8/
      home/
      lexaloffle-pico8.png
      license.txt
      pico-8_manual.txt
      pico8.dat
      pico8.exe
      SDL2.dll
```

**Create container**

In GameNative, click the "+" button and select the `Pico8` folder. Edit container settings as follows:

* General
  * Executable Path: `pico8.exe`
  * Exec Arguments: `-splore -home A:\home`
  * Audio Driver: `PulseAudio`
  * Steam Type: `Ultra Light`
* Controller
  * Disable Mouse Input: `YES`
* Advanced
  * Startup Selection: `Essential`

Graphics settings vary by device. These are my working settings for the Retroid Pocket Classic:

* General
  * Container Variant: `bionic`
  * Wine Version: `proton-9.0-x86_x64`
  * Screen Size: `1024x1024`
* Graphics
  * Graphic Driver: `wrapper`
  * Graphics Driver Version: `System`
  * DX Wrapper: `DXVK`
  * DVVK Version: `async-1.10.3`
  * Sync Every Frame: `YES`
  * Use DRI3: `NO`
* Emulation
  * Box64 Version: `0.3.6`
  * Box64 Preset: `Compatibility`


Save the settings and start the game. Splore should appear; press Back to quit. PICO-8 will create standard subfolders in `home`.

Copy PNG carts into `/Pico8/home/carts` to run them from Splore.

**Screen size**

Regarding the screen size, [Russ from Retro Game Corps explained it perfectly](https://retrogamecorps.com/2024/06/21/native-pico-8-on-android-guide/):
> Pico-8 has a resolution of 128×128. To calculate the appropriate resolution, divide the smallest number of pixels (horizontal or vertical) on your device’s display by 128 and choose the nearest integer (without rounding up). As an example, the Retroid Pocket Classic has a resolution of 1240 x 1080. 1080 / 128 = 8.4375, so 8 is the nearest integer. 8 x 128 = 1024, so you want a custom resolution of 1024 x 1024. This will allow Pico-8 to scale to full screen on the RP Classic. Another example: the Anbernic RG Cube has a resolution of 720 x 720. 720 / 128 = 5.625, so 5 is the nearest integer. 5 x 128 = 640, so you want a custom resolution of 640 x 640.

**Beacon Game Launcher**

In [Beacon Game Launcher](https://play.google.com/store/apps/details?id=com.radikal.gamelauncher), add a platform with these settings:

* Platform type: `Custom`
* Name: `PICO-8`
* Short name: `P8`
* Player app: `GameNative`
* Rom folder: `/Pico8/home/carts`
* (optional) Box art aspect ratio: `2:3` (I like to use custom covers).
* Advanced
    * Use custom launch
    * am start command: _exactly as below_

```
am start -n app.gamenative/app.gamenative.MainActivity -a app.gamenative.LAUNCH_GAME -e cart {file_path}
```

**ES-DE**

To use PICO‑8 with ES‑DE, place PICO-8 carts into the correct ES‑DE `ROMs/pico8` folder, add that folder as a mapped drive in GameNative, and update the `<ES-DE>/custom_systems/es_*.xml` files, which is out of scope for this guide.

**Splore**

To add Splore to a game launcher, export the container from GameNative and add it to your launcher as a Windows Game. Or create an empty file named `splore.png`, any filename containing `splore` will launch Splore.

