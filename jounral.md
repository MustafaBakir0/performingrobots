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