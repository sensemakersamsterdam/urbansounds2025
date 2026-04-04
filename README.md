# urbansounds2025

In this repo we present the script for the urban sounds sensor we have developed with Sensemakers. This is the third version of the sound sensor. It was developed in spring 2025. Two scripts can be used, but it is advised to use the latest version 3.6, that was developed in March '26.

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

Install portaudio en pyaudio:

`sudo apt install python3-pyaudio`

`sudo apt install portaudio19-dev python3-dev`

`pip install pyaudio`

Clone the repo:

`git clone https://www.github.com/sensemakersamsterdam/urbansounds2025` 

`cd urbansounds2025`

Install the packages with:

`pip install -r requirements.txt`

Change the settings in the script urban_sounds_v3.6.py: 
- dev_id 
- topic

Create a file  `config.py` to store the MQTT credentials: 
```
# MQTT variables 
mqtt_host = "sensemakersams.org"
mqtt_user = "your_user_name"
mqtt_password = "your_password"
```
#OpenWeatherMap API key
As (strong) winds disrupt the quality of the sample (you hear only noise) we are interested in the wind speed. Get your free API key at https://www.openweathermap.org. This is optional, the script also works without getting the wind data.

Run the script `urban_sounds_v3.6.py`. You can use the following command:
`nohup taskset -c 0-1 python urban_sounds_v3.6.py`

(`nohup` = no hangup, ensures your remote connection stays open. `taskset -c 0-1` ensures you use two of 4 cores to prevent overusage of the Pi's CPU)

The first time you will run the script it will download the CLAP model from Huggingface (automatically).
Also, after starting up the classification process must 'warm up' so this will take a minute or so. Then classification will go automatically.

You can change the setting `SAVE_RECORDING = False` to True if you want to record .wav files. 

N.B. This script is made for a Raspberry Pi, but it will also run on other hardware. The cpu_temp function will raise an exception, this is only for RPi. 

### Short description of the script.
The script uses two threads: one for recording the audio and one for classification and sending the results over MQTT.

## A short video on CLAP AI model
[https://www.youtube.com/watch?v=dPcVhHVIoIs](https://www.youtube.com/watch?v=dPcVhHVIoIs)
