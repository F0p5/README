# Raspberry Pi project 
## Kettle Twitter Bot
### Student Number 2663592
### Date : 16/03/2022

#### Introduction
The motivation for this project was to create a Kettle that was connected to a Twitter bot so whenever the Twitter bot tweets something the kettle turns on. And as I am 
big fan of making tea sometimes I’m too bored to get up and put the water in the kettle and boil it so this will hopefully help me out so much.

### SAFETY!!!
NOTE: Working with Wires and electricity is dangerous and so all work with the Wires and electricity was carried out in class and under teacher supervision only! 
No work with the wires and electricity was done at home!

### Physical - Construction
The Raspberry Pi is a small computer that runs the Raspbian operating system (which is a Linux distro).
Because the system would be headless, it was required to flash the SD card with Raspbian and save the wi-fi login data to the boot drive. 
It took some effort to connect the pi to the wi-fi network, but after it was done, it was pretty straightforward to connect to the pi via the terminal.
Although I had some issues connecting the pi at first because some technical issues happened with my phone which is an iPhone and the IOS system does not allow you to see 
to see the I.P addresses of people connected to your hotspot.

### Virtual - The code 
Tweepy was used to send the tweets and the bot was used to send the tweets and the kettle would turn on 


### Ideas for version 2 
Now that the kettle can boil the water using the bot there are a couple of ideas i would like to implement into the 2nd version 
For example, the kettle would turn on every day at 6:30AM and it could be done by scheduling the bot to tweet at the kettle every morning

### Conclusion
In the end the project worked, and I hope you liked it. whenever the bot tweeted at the kettle, the kettle would boil the water straight away with the user just casually chilling in the living room. It may sound to a lot of people quite easy but the amount of thinking that goes into such a simple project as well as the wiring is mental



# Import the necessary modules
import os
import tweepy as tp
from time import sleep

# This function Turns the kettle on and off
def switch(x):
    # x = True for "on" and x = False for "off"
    try:
        import RPi.GPIO as GPIO
        GPIO.setwarnings(False)
        Relay_Ch3 = 21
        GPIO.setmode(GPIO.BCM)
        GPIO.setup(Relay_Ch3, GPIO.OUT)
        if x:
            GPIO.output(Relay_Ch3, GPIO.LOW)
        else:
            GPIO.output(Relay_Ch3, GPIO.HIGH)
    except:
        if x:
            print("ON")
        else:
            print("OFF")

# These keys are what connect the Bot to the kettle which allows to turn on whenever it tweets
    consumer_key = 'HlQycNjwdrnOrDA4lBRQjSJnTy'
    consumer_secret ='YxDYfqyWSI3cW6Jxe8O6hwULxxsetwz5BTCVdw8H2jCCTLwef9'
    access_token = '1435789906878545920-o6ziDp3TKyBXLtl46GBLR63hZBOmK6'
    access_secret = '6TXCsID53rD5TexSaL7nu4fpggFO8stbXtnxOvjxxLhzg'
auth = tp.OAuthHandler('HlQycNjwdrnOrDA4lBRQjSJnT','YxDYfqyWSI3cW6Jxe8O6hwULxxsetwz5BTCVdw8H2jCCTLwef9')
auth.set_access_token('1435789906878545920-o6ziDp3TKyBXLtl46GBLR63hZBOmK6','6TXCsID53rD5TexSaL7nu4fpggFO8stbXtnxOvjxxLhzg')
api = tp.API(auth)
tweet = ("Turn the Kettle on now please ")
api.update_status(status=tweet)

