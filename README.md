# Software for CO2 Monitor with MQTT support
This is a fork of "dmage/co2mon". Please see the original repository for further details and updates.
The functionality should be identical to the original software with the addition of the MQTT support. For the MQTT client the [mongoose library](https://github.com/cesanta/mongoose) is used. 

It has been tested with the TFA Dostmann AirCO2ntrol Mini connected to a Raspberry Pi 3 B running Raspbian. The identical device is sold by different resellers and with varying names.

## Compiling

### Prerequisites
#### Ubuntu / Raspbian
sudo apt-get install cmake make g++ pkg-config libhidapi-dev

#### Arch
sudo pacman -S cmake make gcc hidapi

### Compilation
```
mkdir build
cd build
cmake ..
make
./co2mond/co2mond
```

## Usage of MQTT client
```
./co2mond -ma IP-address:port
```
Parameter "m" activates the MQTT client.
If parameter "a" is not provided the address and port of the MQTT server will default to "localhost:1883".

Temperature (degree Celsius) and CO2 (ppm) data will be sent to the MQTT topics:
* "/CO2mon/temp"
* "/CO2mon/CO2"
