# Better Telemetry - Loop Timer 3

Loop Timer 3 uses the Telemetry class in a different way.

```
    public void runOpMode() {
        // (driver presses INIT)
        telemetry.addData("Status", "Initialized");
        telemetry.addData("Test", "Loop timer using TelemetryItems");
        telemetry.update();

        telemetry.setAutoClear(false);
        Telemetry.Item avgItem = telemetry.addData("average" , "%12.3f", 0.0);

        // (driver presses PLAY)
        waitForStart();

        // Create a MovingAverageTimer object so that we can time each iteration of the loop
        MovingAverageTimer avg = new MovingAverageTimer();

        // loop until the end of the match (driver presses STOP)
        while (opModeIsActive()) {

            // Update and recalculate the average
            avg.update();

            avgItem.setValue("%12.3f",avg.average());
            telemetry.update();

            // Allow other threads their fair share of the CPU
            idle();
        }
    }
```

It uses the Telemetry class using addData\(\) during INIT

```
telemetry.addData("Status", "Initialized");
telemetry.addData("Test", "Loop timer using TelemetryItems");
telemetry.update();
```

But then sets the autoClear flag to false and creates a Telemetry.Item

```
telemetry.setAutoClear(false);
Telemetry.Item avgItem = telemetry.addData("average" , "%12.3f", 0.0);
```

To update the value in the loop it uses

```
avgItem.setValue("%12.3f",avg.average());
telemetry.update();
```

If you run the Loop Timer 3 OpMode you will see something like:

![](/assets/LoopTimer3.png)

The average is now 0.016 milliseconds per loop which is equivalent to 62,000 loops per second.



