# urbansounds2025

In this repo we present the script for the urban sounds sensor we have developed with Sensemakers. This is the third version of the sound sensor. It was developed in spring 2025.

## Hardware
- A raspberry pi 5 or 4
-   You will need at least 4 Gb of RAM 
- A microphone. We use an UMIK.
- An all weather casing.

## How to start
**Tested with python 3.11 and 3.12**

Create a virtual environment:

`python -m venv urbansounds`

Activate it:

`source urbansounds/bin/activate`

Install portaudio:

`sudo apt install portaudio19-dev`

Clone the repo:

`git clone https://www.github.com/sensemakersamsterdam/urbansounds2025` 

`cd urbansounds2025`

Install the packages with:

`pip install -r requirements.txt`

Change the settings in the script urban_sounds_v3.5.py: 
- dev_id 
- topic

Create a file  `config.py` to store the MQTT credentials:
```
# MQTT variables 
mqtt_host = "sensemakersams.org"
mqtt_user = "your_user_name"
mqtt_password = "your_password"
```

Run the script `urban_sounds_v3.5.py`

The first time you will run the script it will download the CLAP model from Huggingface (automatically).
Also, after starting up the classification process must 'warm up' so this will take a minute or so. Then classification will go automatically.

You can change the setting `SAVE_RECORDING = False` to True if you want to record .wav files. 

N.B. This script is made for a Raspberry Pi, but it will also run on other hardware. The cpu_temp function will raise an exception, this is only for RPi. 


### Short description of the script.
The script uses two threads: one for recording audio and one for classification and sending the results over MQTT.
