# Switch to the tutorial02 branch

Switch to the tutorial02 branch \(See [Tutorial 1](/tutorial1/switch-to-the-tutorial1-branch.md)\). Once you have checked out the tutorial02 branch your TeamCode folder should look like:

![](/assets/tut2project1.png)

This has all the files from Tutorial 1and also some additional classes from the FGCExamples directory in FgCommon. These classes make writing an OpMode easier to write and handles error conditions better.

You might also want to look at the LoopTimer\[1-3\] classes. They each have the @Disabled annotation meaning they will not populate the OpMode menu on the DriverStation.

The FGCExamples project directory is shown below:

![](/assets/tut2project2.png)

You will see that the FGCExamples teamcode package is split into configurations and opmodes. They use configurations to store information about the robot and the opmodes use a configuration to control the robot. In this way you can re-use a configuration of a robot to create different OpModes.

In this tutorial we will follow the FGCExamples lead and create a configuration for EskyBot

