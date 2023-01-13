# exercise_bike
Monitors target and current exercise bike speed, user-selected workout.

## Components:
- TM1637 Display
- Hall effect sensor
- Rotary encoder w/switch (KY-040 module)
- Nano or Trinket m0?

## Libraries:
- FreqCount or FreqMeasure
- TM1637Display
- RunningAverage

## Program states:
### State 1 - Select mode
- Rotary encoder: Cycle through 1x4 arrays of base 3 elements to select workout 
- {1: low speed, 2: medium speed, 3: high speed}
- Button: Click button to select and continue

### State 2 - Select length
- Left two numbers blink
- Rotary encoder: select higher/lower number by 5 (or adaptive)
- Button: Select workout length (minutes)

### State 3 - Select intensity
- Right two numbers blink
- Rotary encoder: select higher/lower number by 5 (or adaptive)
- Button: Select max speed (mph)

### State 4 - Monitor progress
- Left two numbers: target speed (mph)
- Right two numbers: current speed (mph)
- To show numbers: display.showNumberDec(1512, true); 
- If abs(target - current) > threshold, flash dots
- To flash the dots: dots parameter = 0x40
- Workout length is divided into 4 sections (first and last 2 minutes are warm/cool)
- target speeds for each section are scaled on max speed

## Functions
- Convert workout array to display
 - Detect current speed (convert rpm to mph)
