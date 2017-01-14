***************************************************************
* Arduino PID Library - Version 1.1.1
* by Brett Beauregard <br3ttb@gmail.com> brettbeauregard.com
*
* This Library is licensed under a GPLv3 License
***************************************************************
#THE BASICS
What Is PID?

From Wikipedia: "A PID controller calculates an 'error' value as the difference between a measured [Input] and a desired setpoint. The controller attempts to minimize the error by adjusting [an Output]."

So, you tell the PID what to measure (the "Input",) Where you want that measurement to be (the "Setpoint",) and the variable to adjust that can make that happen (the "Output".) The PID then adjusts the output trying to make the input equal the setpoint.

For reference, in a car, the Input, Setpoint, and Output would be the speed, desired speed, and gas pedal angle respectively.

#Tuning Parameters

The black magic of PID comes in when we talk about HOW it adjusts the Output to drive the Input towards Setpoint. There are 3 Tuning Parameters (or "Tunings"): Kp, Ki & Kd. Adjusting these values will change the way the output is adjusted. Fast? Slow? God-awful? All of these can be achieved depending on the values of Kp, Ki, and Kd.

So what are the "right" tuning values to use? There isn't one right answer. The values that work for one application may not work for another, just as the driving style that works for a truck may not work for a race car. With each new application you will need to try Several Tuning values until you find a set that gives you what you want.

Note: there is also now a PID Autotune Library that can help you determine tuning parameters.

Should I Use PID?

PID is a pretty impressive control algorithm, but it's not magic. You should at least be able to answer "yes" to these questions:

Is it worth the extra work? If you're using a more basic system and it's working for you, there's no real reason to use PID.
Is your system repeatable? The PID needs some semblance of repeatability. When the output is changed from A to B, at least roughly the same thing should happen every time. (think of a car where you step on the gas and sometimes you speed up and sometimes you slow down. not repeatable, not a place where you could use PID)
(This list will probably grow as I think of more criteria. These are the big ones though)

A Note About Relays

Even though a PID controller is designed to work with an analog output, it is possible to connect to a discrete output such as a relay. Be sure to look at the RelayOutput example below.

Questions?
Try the newly created Google group.

The Library
Using The PID Library has two benefits in my mind

There are many ways to write the PID algorithm. A lot of time was spent making the algorithm in this library as solid as any found in industry. If you want to read more about this, check out this detailed explanation.
When using the library all the PID code is self-contained. This makes your code easier to understand. It also lets you do more complex stuff, like say having 8 PIDs in the same program.
