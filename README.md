# BeagleBone

measure the frequency on python

num_pulses = 10 # make this longer for more accuracy
state = GPIO.input("P8_11") # read current input state
while GPIO.input("P8_11") == state:
    pass # wait for input to switch
start = time.time()
for i in range(num_pulses):
    while GPIO.input("P8_11") != state:
        pass # wait for input to switch again
    while GPIO.input("P8_11") == state:
        pass # wait for input to switch again
duration = time.time() - start # this is the duration of num_pulses pulses
period = duration / num_pulses
