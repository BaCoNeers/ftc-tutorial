|  |  |  |  |
| :--- | :--- | :--- | :--- |
|  |  |  |  |

# Decoding OpModes using LoopTimer1

We will use the LoopTimer1 class to examine the components of an OpMode. The code block below represents the entirety of the LoopTime1 class.

```
package org.baconeers.opmode;

import com.qualcomm.robotcore.eventloop.opmode.LinearOpMode;
import com.qualcomm.robotcore.eventloop.opmode.TeleOp;

import org.baconeers.utils.MovingAverageTimer;

@TeleOp(name = "Loop Timer 1", group = "Tests")
//@Disabled
public class LoopTimer1 extends LinearOpMode {

    @Override
    public void runOpMode() {
        // (driver presses INIT)
        telemetry.addData("Status", "Initialized");
        telemetry.addData("Test", "Loop timer using MovingAverageTimer.averageString()");
        telemetry.update();

        // (driver presses PLAY)
        waitForStart();

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
    }
}
```

## Packages

```
package org.baconeers.opmode;
```

Java uses packages to group classes together and avoid name clashes between class names. The package statement must be consistent with the location of the java file on the file system. In this case the java file is in:

```
D:\AndroidStudio\projects\EskyBot\TeamCode\src\main\java\org\baconeers\opmode\LoopTimer1.java
```

The filename can be logically split into the following elements to see how the package name relates to the location on disk.

| Project Java Source Directory | Package Path | Java Source File |
| :--- | :--- | :--- |
| D:\AndroidStudio\projects\EskyBot\TeamCode\src\main\java\ | org\baconeers\opmode | LoopTimer1.java |

## Imports

```
import com.qualcomm.robotcore.eventloop.opmode.LinearOpMode;
import com.qualcomm.robotcore.eventloop.opmode.TeleOp;

import org.baconeers.utils.MovingAverageTimer;
```

The import statements import other class definitions or packages into this class. Android Studio usually fills out the imports for you. Classes inside the same package do not need an import statement, they are implicitly imported.

## Tele-Op / Autonomous Annotations

```
 @TeleOp(name = "Loop Timer 1", group = "Tests")
//@Disabled
```







