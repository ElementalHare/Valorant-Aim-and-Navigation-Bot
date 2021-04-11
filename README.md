# Valorant-Aim-and-Navigation-Bot

**For educational purposes in image processing, serial communication, and other**
Please use within reason: practice range, user hosted testing enviorments.  I am not responsible for your ban.

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

The follow found in mouseHost.py should be scaled to your monitor's resolution.  (Not PC running Valorant's resolution)
```
mon_width = 3840
mon_height = 2160
```

valkset.json
```
{"host-ip": "IP of Mouse Host", "host-port": "6767", 
"client-ip": "IP of PC Running Valorant", "client-port": "6767"}
```
## Usage

Verified to work with Windows.

Run on machine running Valorant
```
./valkyrie.py
```

Run on machine hosting mouse inputs
```
./hostHouse.py
```

## Thanks

Thanks to all those who made this possible with simple to use python packages.  If I missed any license or credits, please let me know and I'll add them here.
