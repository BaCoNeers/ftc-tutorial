# The Project Files

Once you have switched to the tutorial01 branch you should see something like to following in the top left of Android Studio.

![](/assets/tut1project1.png)

There are 4 main elements here:

* **FGCExamples** is some example code from the FGC 2017 season we will look at in a later tutorial
* **FtcRobotController **is the actual RobotController app that gets installed onto the RobotController. Most of this is unmodifiable by you and it is unlikely you will ever need to make changes in this folder.
* **TeamCode **is where you will edit your code, it is merged and transferred to the RobotController with the RobotController app. 
* **Gradle Scripts** contains the gradle build scripts for the app. It is unlikely you will need to edit these files.

## Op Modes

You write your robot code as Op Modes. There are two types of Op Modes, Autonomous and TeleOp and these are used for the Autonomous and TeleOp stages of the FTC game respectively.

The two types of OpModes are only different in that they appear in different menus on the Driver Station. Writing programs for each is the same process.

This project includes 3 OpModes which explore measuring loop timing and using the Telemetry class. They will be used to describe how the Op Mode is run and where to put your code.

If you expand the TeamCode folder in Android Studio, as in the picture below, you will see three classes in the org.baconeers.opmode package; LoopTimer1, LoopTimer2 and LoopTimer3. There is also another class called MovingAverageTimer org.baconeers.utils which calculates a moving average of the time between each iteration of the loop and some other useful information.

![](/assets/tut1project2.png)

