# Jetson Mycroft

## Description
Guide for installing MycroftAI on Jetson AGX Xavier

## Set default microphone and speaker
* pactl list sinks short
* Note microphone you want to use
* pactl set-default-sink DESIRED-NUM
* pactl list source short
* Note speaker you want to use
* pactl set-default-source DESIRED-NUM 

## Install mycroft-core
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

## Set up python
* NOTE: dev_setup.sh sets up a virtual environment to use mycroft with.  
    * This virtual environment did not work for me.
    * I set up the system python to work with mycroft instead
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

## Set up mycroft device
* Ensure you are connected to the internet
* Edit start-mycroft.sh
    * Replace line 83: 
        * source ${VIRTUALENV_ROOT}/bin/activate
    * With 
        * echo "Using system python" # source ${VIRTUALENV_ROOT}/bin/activate
* ./start-mycroft.sh debug
    * If command line states "Changing ownership of /opt/mycroft to user:" and asks for sudo password
        * Hit Ctrl+C: don't give it your sudo password
        * This causes some permission issue, not sure why
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
* ./start-mycroft.sh restart all
* ./stop-mycroft.sh

## Test Mycroft
* ./start-mycroft.sh debug
    * If command line states "Changing ownership of /opt/mycroft to user:" and asks for sudo password
        * Hit Ctrl+C: don't give it your sudo password
        * This causes some permission issue, not sure why
* Speak: "Hey Mycroft"
* Wait for confirmation sound
* Speak: "What's the weather like?"
* Listen for response
* quit (Ctrl+C)
* ./stop-mycroft.sh