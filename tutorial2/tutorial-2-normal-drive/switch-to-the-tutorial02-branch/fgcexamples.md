# FGCExamples

The FGCExamples project directory is shown below:

![](/assets/tut2project2.png)

You will see that the FGCExamples teamcode package is split into configurations and opmodes. They use configurations to store information about the robot and the opmodes use a configuration to control the robot. In this way you can re-use a configuration of a robot to create different OpModes.

In this tutorial we will follow the FGCExamples lead and create a configuration for EskyBot

## FGOpMode

The FGOpMode class extends the LinearOpMode we used in Tutorial 1.

```
/**
 * OpMode Abstract class that offers additional abstraction for opMode developers 
 * including catch-all error handling
 */
public abstract class FGOpMode extends LinearOpMode {
```

It overrides the runOpMode\(\) method and adds some error handling to catch exceptions and send the information to the Driver Station and continues running. This is important because _any _exception thrown in the stock runOpMode causes the OpMode to exit. This can save a lot of time trying to work out what threw the exception - you can just try again, without having to restart.

To use the FGOpMode class you must provide implementations for onInit\(\) and activeLoop\(\). You can also override onStart\(\) to do one off operations after start is pressed.

The new runOpMode\(\) method does the same things we did in Tutorial 1 with LinearOpMode.  You can see where onInit\(\), onStart\(\) and activeLoop\(\) are called below. Note that we no longer need to call telemetry.update\(\) or idle\(\) this is done for us.

```
    @Override
    public void runOpMode() throws InterruptedException {

        try {
            setup();
            onInit();
        } catch (Throwable e) {
            ErrorUtil.handleCatchAllException(e, telemetry);
        }

        waitForStart();

        onStart();

        while (opModeIsActive() && !operationsCompleted) {

            try {
                activeLoop();
            } catch (Throwable e) {
                ErrorUtil.handleCatchAllException(e, telemetry);
                ;
            }

            telemetry.update();
            idle();
        }

        //wait for user to hit stop
        while (opModeIsActive()) {
            idle();
        }
    }
```

## RobotConfiguration





