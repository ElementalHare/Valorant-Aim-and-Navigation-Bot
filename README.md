# Valorant-Aim-and-Navigation-Bot

**For educational purposes in image processing, serial communication, and other**
Please use within reason: practice range, user hosted testing enviorments.  I am not responsible for your ban.

## How it works?

This is a color based aimbot made in python that works in fullscreen mode.  It has multiple color filterings that will automatically adjust itself when a target is detected.  Target detection occurs when the right color is seen by the first filter on a large fov detection range.  The second filter applies once the conditions for the first is met; detection range reduces and color filtering becomes much more lenient.  Because the head of enemy characters are usually the highest point, we scan from top left to bottom right and the first instance of purple pixel found, filtering switches to a more accurate mode and smaller fov resulting in quicker detection on the second pass when looping through the pixel array.  The size of the fov is determined if `Shift` is held down or not, auto recoil compenstation is implemented.

## Limitations

This demonstration requires 2 seperate computers and 2 seperate arduino units.  Computing speed depends on PC, but is relatively and optimized for speed.  Works only with 1080p screen size on Valorant PC

## Setup

```
pip3 install opencv-python==4.3.0.36
pip3 install mss==6.0.0
pip3 install numpy==1.19.0
pip3 install keyboard==0.13.5
pip3 install pyserial==3.4
pip3 install sockets==1.0.0
pip3 install scikit-image==0.16.2
```

The follow found in **mouseHost.py** should be scaled to your monitor's resolution.  (Not PC running Valorant's resolution)
```python
mon_width = 3840
mon_height = 2160
```

**valkset.json**
```json
{"host-ip": "IP of Mouse Host", "host-port": "6767", 
"client-ip": "IP of PC Running Valorant", "client-port": "6767"}
```

Flash the respective arduino files per arduino, afterwards com ports may need to altered accordingly

valkyrie.py
```python
serMouse = serial.Serial('COM3', baudrate=2000000, writeTimeout=0)
serKeyboard = serial.Serial('COM4', baudrate=2000000, writeTimeout=0)
```

How files and arduinos should be arranged
```
PC 1
├── valkyrie.py
└── valkset.json
```

```
PC 2 (Running Valorant)
├── mouseHost.py
├── Arduino For Mouse Emulation
└── Arduino For Keyboard Emulation
```

Valorant settings should be as follows
* Set Game to 0.5 sense
* Set Game to 0.84 or 0.85 zoom sense, 0.9 to tracking moving targets (Weapon Dependent)
* Set Game to 1920 x 1080
* Set Game to Show Purple
* Set Game to Hide Corpses
* Set Game to Transparent Cursor
* Set Game FPS to MAX
* Set Walk to P (secondary)
* Set Zoom to O (secondary)
* Set Move Up to Up Arrow
* Set Move Down to Down Arrow
* Set Move Left to Left Arrow
* Set Move Right to Right Arrow
* (Optional) Set AA to MSAA 4x for long range precision

## Usage (Startup)

Verified to work with Windows.

Run on machine running Valorant
```
./valkyrie.py
```

Run on machine hosting mouse inputs
```
./hostHouse.py
```

## Usage (Mouse Host PC)

* Press ``` - ``` Key to exit
* Press ``` ` ``` Key to pause mouse lock/ grabber
* Press ``` ESC ``` Key to unpause

## Usage (Valorant PC)

* Modes
  * Press ``` ` ``` Key to pause and go into mode selector
  * Press ``` ESC ``` Key to engage Mode 1: Automatic Auto Aim
  * Press ``` F1 ``` Key to engage Mode 2: Auto Aim when shoot button is triggered, slowly moves camera towards target
  * Press ``` F2 ``` Key to engage Mode 3: Auto Aim when shoot button is triggered, snaps to target and snaps back immediately, resulting effect should be (mostly) unoticable.
* Other
  * Hold ``` [ ``` or ``` ] ``` Key to temporily pause detection and auto aim when in Mode 1
  * Hold ``` Shift ``` Single Shot
  * Release ``` Shift ``` Spray and Pray
* Settings
  * Look in terminal for guidence
  
## Thanks

Thanks to all those who made this possible with simple to use python packages.  If I missed any license or credits, please let me know and I'll add them here.
