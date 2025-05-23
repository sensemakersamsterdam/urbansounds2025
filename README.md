# urbansounds2025

In this repo we present the script for the urban sounds sensor we have developed with Sensemakers. This is the third version of the sound sensor. It was developed in spring 2025.

## Hardware
- A raspberry pi 5 with 16Gb RAM (8Gb might be fine too)
- A microphone. We use an UMIK.
- An all weather casing.

## How to start
Clone the repo

Create a virtual environment:

`python -m venv urbansounds`

Activate it:

`source urbansounds/bin/activate`

Install the packages with:

`pip install -r requirements.txt`

Change the settings: 
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

You can change the setting `SAVE_RECORDING = False` to True if you want to record .wav files. 

N.B. This script is made for a Raspberry Pi, but it will also run on other hardware. The cpu_temp function will raise an exception, this is only for RPi. 


### Short description of the script.
The script uses two threads: one for recording audio and one for classification and sending the results over MQTT.
