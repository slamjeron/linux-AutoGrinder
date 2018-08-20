### linux-AutoGrinder
## Synopsis

The purpose of "Auto Grinder" is to automate repetitive tasks on the computer. Built for games or business applications, I have used it to play a game called "Dark Orbit". This program will only work on a Linux operating system. Tested most with the Ubuntu operating system.

## Code Example

To record what the user does I use the library pynput which can access and use input then I place it in a list to be played back later.


This code determines what happens when you type a key or click the mouse using the library pynput.

    def on_click(self, x, y, button, pressed):
        global recording

        if recording == True:
            if pressed:
                if self.up == True:
                    self.up = False
                    pnt = int(x), int(y)
                    lis = [0, self.pl.getMilsec(), pnt, '']
                    self.pl._array.append(lis)
                    self.pl.millsec = 0
            else:
                self.up = True

    def on_key_press(self, keyCode):
        global recording
        global playing
        key = str(keyCode).strip('\'')
        key = str(key).replace('Key.', '')
        if key == self._endComand:

            self.stopAll()
            return False
        elif key == self._stRecordCommand and recording == False and playing == False:
            self.record()
        elif key == self._playRec and recording == False and playing == False:
            print('play key hit')

            #self.pl is the Player class a thread that plays the recording and keeps track of time.
            #the commands below help the player class know what to do.
            self.pl.slowing = False
            self.pl.speedUp = False
            self.pl.delete = False
            self.pl.insertClick = False
            self.pl.pause = False
            print('playing intems = false')
            self.play()




## Motivation

Auto Grinder was created to remove repetitive tasks from my life.  I currently use a java program I built to play a game called Dark Orbit. When I got new computers, I set them up with Ubuntu, and for the life of me I could not get the program I had developed to work with the Linux operating system.

## Installation
To install Auto Grinder, click <a href="https://github.com/slamjeron/linux-AutoGrinder/raw/master/autogrinder2/dist/advanstAutoGrinder.zip" download="advancedAutoGrinder">advansed auto grinder</a>, unzip the file, double click on the folder and then
right click inside the folder, click Open in Turminal, then type sudo ./advanstAutoGrinder press enter then a terminal window should open. Then you are free to record and play macros. This program will only work on a Linux operating system. Tested most with the Ubuntu operating system.

## API Reference
To build Auto Grind I used pynput to get user input, pyautogui to simulate user input, Pickle to save my programs information.

## Tests
This will start the program
def main():
    con = GuiCon()
    con.start()
    return 0


main()

this code keeps track of user input

    def on_click(self, x, y, button, pressed):
        print (x,y)


    def on_key_press(self, key_code):
        print (key_code)
these are the main functions

## Contributors

Auto Grinder has many key commands that you will need to know
in both the advanstAutoGrinder and the comandcontroler the following hot keys are active,
"-" key will increase the speed of the next action "+" key will decrees the speed of the next action,
"Q" will stop the recording and play back "R" starts recording "P" starts playing back your recording
"ESC" will stop the program though to complete the closing proses you must ether close the program or type something in the terminal.

# commands for advanstAutoGrinder
"0" Key will paus play back so you can edit the current action right arrow key will make you go to the pervious action left
arrow key will make you go to the next action. Currently you may not resume the play back you must press "Q" then "P" to start
the sequence over. When paused type 2 too add a click to the current index. Too replace an action type 3 and where ever your curser is it will click their next time the record is played.


## License

This program is an open source program.
