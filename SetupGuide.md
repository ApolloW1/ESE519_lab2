# ESE519_lab2
Machine: MacBook Pro Apple M1 Pro
MacOS 13.0 (22A380)
## 1. Pico Setup
In this setp, the pico directory will be created.
Command:

$ wget https://raw.githubusercontent.com/raspberrypi/pico-setup/master/pico_setup.sh 

$ chmod +x pico_setup.sh

$ ./pico_setup.sh

$ sudo reboot

## 2. Installing toolchain
### 2.1 Install Homebrew
Command:

$ /bin/bash -c "$(curl -fsSL
https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

$   
    echo '# Set PATH, MANPATH, etc., for Homebrew.' >> /Users/apollo/.zprofile
    
    echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/apollo/.zprofile
    
    eval "$(/opt/homebrew/bin/brew shellenv)"

### 2.2 Install toolchain
Command:

$ brew install cmake

$ brew tap ArmMbed/homebrew-formulae

$ brew install arm-none-eabi-gcc

## 3. Saying Hello World in C
### 3.1 Build "Hello World"
Enter into hello_world file and then make.Two separate examples programs will be built in the hello_world/serial/ and hello_world/usb/ directories.

Command:

$   cd pico

$ cd pico-examples

$ mkdir build

$ cd build

$ export PICO_SDK_PATH=../../pico-sdk

$ cmake ..

$ cd hello_world

$ make -j4
### 3.2 Run "Hello World" 
Connect RP2040 to the laptop with a micro-USB cable, while holding down BOOTSEL button. After being connected, release BOOTSEL button and drag-and-drop either the hello_serial.uf2 or hello_usb.uf2 onto the Mass Storage Device.RP2040 will reboot and begin to run the flashed code. 

cp -X blink.uf2 /Volumes/RPI-RP2/
### 3.3 See "Hello World" Output

Find the device name by

$ ls /dev/tty.*

Connect to the serial console

$ screen /dev/tty.usbmodem1101 115200


![IMG_9743](https://user-images.githubusercontent.com/114015725/194969363-413a4ee0-078f-4072-9cf1-d4deac72ad57.jpg)

