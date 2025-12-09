We started with the basics: cutting a 40 by 40 cm wooden board that would serve as the robot’s base. After that, we drilled holes to attach the front wheel, followed by more drilling to mount the motors and rear wheels. The wheels initially had torn rubber, so we replaced them to make sure the robot could move smoothly. Once everything was in place, we added holes for the battery and Arduino, securing them firmly to the board.

With the hardware set up, it was time to bring the robot to life through code. We began by programming it to move back and forth to test the motors. Once that worked, we connected a radio signal receiver and used a controller to send input commands to the Arduino, allowing us to control the robot’s movement remotely.

At first, the motors were very stiff,  they would either move at full speed (255) or not at all (0). When I stopped the wheels, they would just lock up and drag along the floor. To fix this, I implemented a linear interpolation algorithm that smoothed the transition between different speed levels, making the movement much more natural and gradual.

After that, we worked on turning. The robot could now change direction by slowing down or stopping one wheel entirely while the other kept moving, allowing it to pivot smoothly in the desired direction.

By the end of these eight weeks, what started as a simple wooden board had turned into a fully functional, remote-controlled robot — and I couldn’t be prouder of how far it came.


At first, the motors behaved very “on/off”—it felt like speeds jumped straight from 0 to 255. When I stopped, the wheels would lock and drag, which looked rough and wasn’t great for traction.

I fixed this by adding a linear interpolation step that eases the current speed toward the target speed over time. Instead of jumping to a new value, the motor command blends gradually, which:
- Reduces jerk when starting and stopping
- Improves traction and control
- Makes the robot feel much more responsive and predictable


For turning, I slow down—or even stop—one wheel while keeping the other moving. Small speed differences give gentle curves, and stopping one side produces a tighter pivot. Combined with the smoothing above, turns now feel deliberate rather than abrupt.

we also made the shoulders by screwing a wooden piece and attaching giant servos to act as joints for the shoulders, that is done, it was snooth and easy.

We also added 1 elbow for an arm, and now we have a shoulder and elbow that move in a natural way


Next steps: attach a gripper

the idea of how we should implement the grabber mechanism is i think by attaching it to a piece of a wood and attach that piece of wood to the exisitng shoudler servo motor.

maybe then attach another servo with strings to make it control the gripper?

We also have the idea to have the head as a cylinder and it would have 2 pieces. The outer peice is like a cover with an opening in the front. the inner piece is a clinder with multiple expressions that rotates based on the emtoions the robot is feeling

### 24/10

 had to increase the size of the base. that is a whole hour of unscrewing, screwing, drilling, and cutting wood. this happened because the two servo motors and the shoulder and elbow add so much weight on one of the sides, so now when the robot moves, it tilts and loses balance. we made the base bigger but we didn't incrase its size from the back, so now the robot tilts backwards. I guess a more thorough look about the physics of it could have saved us some time because now we have to add another wheel from the back to balance the robot. This is the kind of mistakes that you only do once because it draws your attention to similar problems next time. overall, progress is awesome.

Next steps, we want to add the rotating head with expressions, i dont think we need a alazy suzan but professor said we might need a giant servo.  I really hope the powerbank we have will be able to power all of those servos we have, we currently have 4 big ones!!

We conceptualized the left arm to be a see through acrylic arm with leds inside that will be a form of expression when talking such that it would change color based on the dialogue appropriately. We cut acrylic pieces anda ttached them together using acrylic glue which smelled horrible but worked for the first week then it detached. We then wanted to use an L bracket to hold everything in place but that broke teh acrylic so we stuck to super glue and let me tell you, super glue STICKS.

then the servo was upside down so it moves backward so we reversed the hub which needed more drilling but now it didn't break te acrylic thankfully.

For the right arm attachments, based on the dialgue, we found that it would make sense to have a beer can for tha party, a toy for talking to the child or making fun of the other attorney, a sword to demonstate aggression and hosititly, and lastly a pen, because saulbot is a laywer. 

Then we made the head with 3 expressions such that the head rotates to the appropriate expression in each scene. First face is a creeper from minecraft becausew why not, the second is a Labubu face, and the third is the money eyes emoji. The robot cycles between those appropriately based on the lines.

For the lines, I wrote the script because I am familiars with our inspriation, saul goodman's character from the famous TV series breaking bad. Then I voiced the robot and distorted my voice using Audacity by lowering the pitch.

Then the added weight made our robot not move so I updated my interpolation function to make the robot drive with more force and faster accelration which fixed it.

We then borrowed clothes from the costume shop and filled them with paper to give saulbot the proper alcoholic build. He's very colorful now.

When the receiver gets a number between 0 and 21, it triggers one of 22 different performance routines that combine specific movements with lighting patterns and audio tracks. The code processes these commands through a single function called processCommand() that routes each number to its corresponding case. The servo motors move smoothly rather than jumping to positions because each joint tracks its current angle and increments toward target positions in small steps. The shoulders have a reset position at 30 degrees, the head centers at 90 degrees, and the elbow starts at 0 degrees for the default pose. The elbow servo has four specific angles corresponding to different attachments: 0 degrees for a pencil, 90 degrees for a sword, 180 degrees for a toy, and 270 degrees for a bottle. The NeoPixel system includes a sophisticated transition mechanism that smoothly fades between different color patterns rather than switching abruptly. I built functions to create solid colors, gradients between two colors, rainbow patterns, alternating colors, and chase effects. The transition system stores current and target colors for each pixel, then interpolates between them frame by frame at a configurable speed. This means when the robot switches from one performance to another, the lights fade gracefully from one mood to the next. The default state keeps a continuously cycling rainbow gradient running in the background through a non-blocking update function called every loop iteration.
The 22 performance cases range from simple to complex.
Case 0 executes a full robot dance party with four distinct phases: wave motions with rainbow cycling, head nodding with pulsing colors, an attachment showcase that cycles through all four arm positions while displaying matching colors, and a grand finale with rapid color changes and coordinated joint movements.

Case 1 raises both shoulders to 90 degrees, moves the elbow to display the toy attachment, then swings the toy arm back and forth for five seconds while blue gradient lighting plays and audio track 001 runs.

Case 2 creates a party atmosphere by moving the pen attachment into position, turning the head 60 degrees, raising the right shoulder, then swinging the pen while rapidly cycling through six different colors (red, green, blue, yellow, magenta, cyan) until the audio finishes.

Case 3 takes an aggressive approach with bright red gradient lighting, raising both shoulders (the left all the way to 180 degrees), positioning the sword attachment, then simultaneously swinging the sword and rotating the head 180 degrees back and forth for five seconds.

Case 4 displays pink gradient waves while raising the right shoulder and swinging the toy attachment.

Case 5 plays track 021 (a special case positioned differently in the sequence) with pink lighting while the left shoulder waves up and down.

Case 6 shows gold gradient lighting while the head swings side to side for five seconds.

Case 7 creates a disapproval gesture by swinging the head left and right while red lights blink on and off every half second for the duration of the audio track.

Case 8 displays orange gradient lighting while raising the right shoulder and swinging the sword attachment.

Case 9 moves the pen into position, raises the right shoulder, then creates a complex performance where the pen swings, the shoulder makes small complementary movements, and green lights blink rapidly, all continuing until the audio completes.

Case 10 creates a striking visual by splitting the LED strip in half, lighting 32 pixels red and 32 pixels green, then blinking this pattern on and off while audio plays.

Case 11 simply rotates the head 45 degrees from center and holds that position.

Case 12 generates excitement by rapidly cycling through all four arm attachments every 400 milliseconds while party lights flash through six colors every 150 milliseconds, creating a frenetic energy.

Case 13 positions the sword attachment, raises both shoulders to 90 degrees, then blinks all lights red while maintaining this pose.

Case 14 moves the head and both shoulders 45 degrees from their reset positions, then immediately returns them to default without waiting.

Case 15 displays red gradient patterns while raising the left shoulder to 90 degrees.

Case 16 creates sharp transitions by cycling through pure red, green, and blue colors every half second (no fading) while raising the sword attachment and right shoulder.

Case 17 turns the head to 60 degrees while very fast green lights blink on and off every 100 milliseconds.

Case 18 positions the sword while slow red lights blink every full second.

Cases 19 and 20 simply play audio tracks 018 and 019 without any movement or special lighting.

Case 21 creates chaos by making all joints move randomly within safe ranges while slow red lights blink every second, continuing until the audio finishes.


The code includes helper functions that make the performance cases cleaner to write. 

The resetRobotPose() function returns all joints to their default positions with deliberate pauses between each joint for a more natural reset sequence. 

The quickResetRobotPose() function does the same thing in about two seconds by using larger step sizes and moving all joints simultaneously. 

The resetShoulderAndHead() function resets only those two joints while leaving the elbow wherever it happens to be. 

The transition functions for NeoPixels (transitionToSolid, transitionToGradient, transitionToRainbow, transitionToAlternating, transitionToOff) provide one-line commands to smoothly change lighting moods. 

The system can handle radio commands arriving wirelessly and serial commands typed into the serial monitor for testing purposes, making development easier since I can trigger any performance without needing the transmitter connected.

The main loop continuously updates the rainbow gradient background animation, checks for serial input, and listens for radio messages, then routes any received command number to processCommand().

The entire system creates a robot that feels alive and responsive, capable of expressing different moods through the coordination of movement, light, and sound.Claude is AI and can make mistakes. Please double-check responses.
