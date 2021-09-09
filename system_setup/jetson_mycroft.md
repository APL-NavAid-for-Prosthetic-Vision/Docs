# Jetson Mycroft

## Description
Guide for installing MycroftAI on Jetson AGX Xavier

## 1) Enable Bluetooth Audio
* Navigate to this file:
    * /lib/systemd/system/bluetooth.service.d/nv-bluetooth-service.conf
* Use a text editor to change this line ...
    * ExecStart=/usr/lib/bluetooth/bluetoothd -d --noplugin=audio,a2dp,avrcp
* ... to this: 
    * ExecStart=/usr/lib/bluetooth/bluetoothd -d 
* Enter these commands to update the apt-get package list and install the pulse audio package:
    * sudo apt-get update
    * sudo apt-get install pulseaudio-module-bluetooth
* Enter this command to reboot the Jetson device:
    * sudo reboot
* When the reboot is complete, pair and connect any Bluetooth headset.
* Source: https://docs.nvidia.com/jetson/l4t/index.html#page/Tegra%20Linux%20Driver%20Package%20Development%20Guide/hw_setup.html#wwpID0E0KN0HA 


## 2) Set default microphone and speaker
* Connect bluetooth headphones
* pactl list sinks short
* Note microphone you want to use
* pactl set-default-sink DESIRED-NUM
* pactl list sources short
* Note speaker you want to use
* pactl set-default-source DESIRED-NUM 

## 3) Install mycroft-core
* cd ~/slamr01_workspace/Software
* git clone https://github.com/MycroftAI/mycroft-core.git
* cd mycroft-core
* bash dev_setup.sh
    * run on master: Y
    * auto update: Y
    * build local mimic: N
    * add path in .profile: Y
    * auto check code-style: Y
* Add the following to your .bashrc:
    * source ~/.profile_mycroft

## 4) Set up python
* NOTE: dev_setup.sh sets up a virtual environment to use mycroft with.
    * This virtual environment did not work for me.
    * I set up the system python to work with mycroft instead
    * Better to use system python anyway for ROS compatability
* pip3 install -r requirements/requirements.txt
* pip3 install -r requirements/extra-audiobackend.txt
* pip3 install -r requirements/extra-stt.txt
* pip3 install -r requirements/extra-mark1.txt
* pip3 install -r requirements/tests.txt
* Add the following to your .bashrc
    * export PYTHONPATH="${PYTHONPATH}:MYCROFTCOREPATH"
    * where MYCROFTCOREPATH is the path of the in mycroft-core folder
    * For me, this was /home/slamr01/slamr01_workspace/Software/mycroft-core
* source .bashrc
* Test mycroft python import
    * cd
    * python3
    * import mycroft
    * quit()
    * cd Software/mycroft-core

## 5) Set up mycroft device
* Ensure you are connected to the internet
* Edit start-mycroft.sh
    * Replace line 83: 
        * source ${VIRTUALENV_ROOT}/bin/activate
    * With 
        * echo "Using system python" # source ${VIRTUALENV_ROOT}/bin/activate
* sudo ./start-mycroft.sh debug
    * Mycroft voice output will not work yet
    * In the HISTORY log, mycroft lists instructions for setting up the device
        * Open browser, navigate to home.mycroft.ai
            * Create account
            * In top right, select menu button, navigate to devices
            * ADD DEVICE
                * Enter pairing code in HISTORY log
                * Enter device name (I used slamr01)
                * Enter device location (I used Laurel, Maryland, US)
                * Select Google Voice (Other options will not work)
                * Select Wake Word (I used Hey Mycroft)
    * quit (Ctrl+C)
* sudo ./stop-mycroft.sh

## 6) Test Mycroft
* sudo ./start-mycroft.sh debug
    * If you get an "Illegal instruction (core dumped)" error, see next step
* Speak: "Hey Mycroft"
* Wait for confirmation sound
* Speak: "What's the weather like?"
* Listen for response
* quit (Ctrl+C)
* ./stop-mycroft.sh

## 7) Downgrade Numpy to resolve "Illegal instruction (core dumped)"
* At somepoint in this processes, you may get a "Illegal instruction (core dumped)" error when running mycroft
* To resolve this error, downgrade numpy from 1.19.5 to 1.19.4
    * pip3 uninstall numpy
    * pip3 install numpy==1.19.4

## 8) Test Mycroft (Again)
* With the "Illegal instruction (core dumped)" error resolved, repeat Test Mycroft step

## 9) Fix Aftershokz Aeropex buzz at wake word
* While running mycroft with the Aftershokx Aeropex, the Aeropex makes a deafening buzz sound after the wakeword
* I have only been able to fix this by editting the Mycroft source code
* Open the mic.py file (for me: /home/slamr01/slamr01_workspace/Software/mycroft-core/mycroft/client/speech/mic.py)
    * Comment out line 734: emitter.emit("recognizer_loop:record_begin")