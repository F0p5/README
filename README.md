# README
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
