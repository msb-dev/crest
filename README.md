# Adafruit MQTT client

Adafruit is a cloud service. Sign up for an account and create a "Feed". You can then push data to this feed in various different ways (e.g. create an IFTTT applet and use the Adafruit service to send data on a particular trigger). You can also query the feed from other places, e.g. from python code running on your Raspberry Pi.

The example code here sets up a loop that keeps checking for new messages to your feed and prints them to your python terminal.

I've used `pipenv` to install python and all the packages this code needs on my computer. If you want to use this too, install `pipenv` on your raspberry pi using the command `pip instal pipenv`. Once that's installed, go to the folder where you put all this code and run the command `pipenv install`. That will install the correct version python (I think 3.8) and the `Adafruit_IO` python package needed to talk to Adafruit's cloud service.

You then need to follow the instructions in the comments in the config_EXAMPLE.py. When that's done, you can run `pipenv shell` to get the right version of python and then run `python main.py` to run this program.

Every time you add some more data to your Adafruit feed, this program should detect the new data and print a message to the terminal.

You can imagine sending data to the feed with the value `leaving-for-work` when you leave the house, and `about-to-arrive-home` when you get near your house. You can then modify the `message` function in `main.py` to check the `payload` variable and either extend or retract the panels depending on the message content (e.g. with an `if` statement).

You should also think about what happens when you loose contact with the the internet and need to reconnect. Think about what happens if you missed any messages when the internet was down. How might you check the feed manually for any missed messages?