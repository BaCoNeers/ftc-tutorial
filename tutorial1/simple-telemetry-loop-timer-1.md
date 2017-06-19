# Simple Telemetry - Loop Timer 1

The Loop Timer 1 OpMode uses the MovingAverage class to measure the interval between loop iterations and then uses the Telemetry class to display the average on the driver station.

```
// Create a MovingAverageTimer object so that we can time each iteration of the loop
MovingAverageTimer avg = new MovingAverageTimer();

// loop until the end of the match (driver presses STOP)
while (opModeIsActive()) {

// Update and recalculate the average
avg.update();

telemetry.addData("Status", avg.averageString());
telemetry.update();

// Allow other threads their fair share of the CPU
idle();
}
```

To run the Loop Timer OpMode, connect the RobotController via USB to your computer and click the AndroidStudio Run button which will build and install the RobotController app onto the RobotController.

![](/assets/run_teamcode.png)

Android Studio may then ask you what device to deploy it on. Select your device and click OK.

![](/assets/run_deploy_target.png)

If this is the first time you have connected the phone may ask you to accept the debug connection first. 

If your controllers are setup properly, the RobotController app should start on the RobotController. 

## RobotController

![](/assets/LoopTimer1_robotcontroller.png)

## Driver Station

You should also have the Driver Station app running on the Driver Station. When they connect the Loop Timer 1 OpMpde should be visible in the TeleOp menu on the Driver Station. Select it, INIT it and then RUN to see something like below:

![](/assets/LoopTimer1.png)

The RobotController is not connected to the robot and so you will see a Warning message similar to above.

You should see the Status message updating with the average loop time. Here is it showing 0.089 milliseconds, each loop is taking only 89 microseconds and equates to about 11,000 loops per second.

You can press stop to stop the OpMode but Android Studio is still connected and so you may need to press stop on Android Studio

