# PiCamGPIO-Telegram
Control GPIO and Pi Camera using Raspberry Pi + Telegram App

The Telegram app is taking the techie community by storm. Maybe not all your friends use it, but it has enough cool features to make it fascinating for people who like to tinker.

Apart from regular features, like chatting, groups, and being able to send pics and short video or audio files, Telegram boasts end-to-end encrypting (no more NSA spying on your chats), cloud-distributed servers (more reliable connections), secret chats, and …

As if that were not enough, Telegram is open source, uses an open protocol, and has a public API, which means that any developer can create new clients for different platforms.

Although it's officially intended for iOS and Android, unofficial ports have been made to Windows Phone, Windows, the web, and the Raspberry Pi's Linux command line, which I will talk about in this article.


## Installation :>

If you have an Android phone or an iPhone, you can get Telegram from Google Play or the Apple App Store. If you haven't done so already, I would advise doing so and setting up an account from your phone before proceeding. To run Telegram from your Raspberry Pi, you are going to have to download the source code and compile it.


## Clone GitHub Repository :

`git clone --recursive https://github.com/vysheng/tg.git && cd tg`


## Install libs :

`sudo apt-get install libreadline-dev libconfig-dev libssl-dev lua5.2 liblua5.2-dev libevent-dev libjansson-dev libpython-dev make`



## Configure :

Regardless of how you decided to get the source, the next step is configuring the makefile for the compile:

`./configure`



make :

Then, start the compile proper:

`make`



Once finished, you should have an executable program called telegram in the tg directory.


## Setup :>

Before you start texting from the command line, you have to connect your Pi to your Telegram account and associate it with your mobile phone number. To do this, run Telegram with the-k option and point it to the public key in the tg directory:

`bin/telegram -k server.pub`

The program then asks you for a code that is sent to your phone via SMS and which you receive in a few seconds after registering.

After entering the code, your connected contacts show up. You will also see a > at the bottom. This is the Telegram command-line prompt, and what you type shows up here.


## Schematic :

The LED is connected to GPIO 27

![image](https://user-images.githubusercontent.com/31132150/152271714-572d118a-c988-4cf7-bbc2-73d5e3c2a6cb.png)


## Run Python Script :

You can specify the python script from command_line [-Z]. For example :

`sudo bin/telegram-cli tg-server.pub -Z pythonscript.py`

make sure that you are running command as a superuser (by using sudo).


## Create a Python Script With the Following Contents :

`sudo nano /home/pi/tg/pythonscript.py`

## Save and exit and then Run :

sudo bin/telegram-cli tg-server.pub -Z pythonscript.py



When incoming text message is led off or led on, Telegram answers us with a text message and led set is OFF or ON. (For more information, see Python script)


## Take Picture :

To take a photo, enter the following command in Telegram app:

`!photo`

Now if you send a text message with !photo, Raspberry answer with a photo.

![image](https://user-images.githubusercontent.com/31132150/152271841-2f2e20c6-ed6e-4c30-a0b2-5e2c2fbb761d.png)

