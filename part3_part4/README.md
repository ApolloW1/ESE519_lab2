# Part 3
A 'sequencer' is achieved by python, which allows to record BOOT button presses and play them on the Neopixel, and also play a sequence of read/write commands.

The sequencer can obtain the value of register from the REPL in part 2 and also write it. User can choose either record or replay mode while setting the record length or the replay loops. 
  
The record will be in json file, while the replay will read the json file and show it by on and off of the Neopixel LED.
