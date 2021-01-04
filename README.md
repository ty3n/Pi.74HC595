# Pi GPIO control 
   ![](https://github.com/ty3n/Pi.74HC595/blob/main/img/1.jpg?raw=true)![](http://172.25.102.61:3000/Nick/Raspberry-pi.GPIO.74HC595/raw/branch/master/img/2.png/)
> As above pi pin, 5,6,13,19,26,12,16,20,21 can control LED_EN, LED_DAT, LED_CLK to implement LED control. 1 pi for 3 station is available. 

### 74HC595 
    Pin Descriptions
* 1 Q1 Parallel Data Output 1
* 2 Q2 Parallel Data Output 2
* 3 Q3 Parallel Data Output 3
* 4 Q4 Parallel Data Output 4
* 5 Q5 Parallel Data Output 5
* 6 Q6 Parallel Data Output 6
* 7 Q7 Parallel Data Output 7
* 8 GND Ground
* 9 Q7S Serial Data Output
* 10 Master Reset Input
* 11 SHCP Shift Register Clock Input
* 12 STCP Storage Register Clock Input
* 13 E Output Enable Input
* 14 DS Serial Data Input
* 15 Q0 Parallel Data Output 0
* 16 VCC Supply Voltage

### Script for 74HC595
```
import RPi.GPIO as IO
rclk = 26 # parallel output, shift high to low to make Q1~7 output
ser = 12 # data input
srclk = 19 # register, shift high to low, make storage and shift to next clock input
IO.setwarnings(False)
IO.setmode(IO.BCM) # BCM for GPIO nummber, BOARD for Pin number
IO.setup(26,IO.OUT) # initialize 
IO.setup(12,IO.OUT)
IO.setup(19,IO.OUT)

for y in range(8):
    IO.output(12, 1) #  pull high data to register
    IO.output(19, 1) #  store data and shift register
    IO.output(19, 0)
    IO.output(12, 0) # clear data

IO.output(26, 1) # Parallel output
IO.output(26, 0)
```

### Script for Button
```
import RPi.GPIO as GPIO
GPIO.setwarings(False)
GPIO.setmode(GPIO.BCM)
GPIO.setup(21, GPIO.IN, pull_up_down=GPIO.PUD_DOWN)
#GPIO.input(21) # read GPIO value while press button or not
while Ture:
    if GPIO.input(21) == GPIO.LOW:
        while True:
            if GPIO.input == GPIO.HIGH:
                print "Button pressed"
                break
```
