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

The **@TeleOp** Annotation is needed for the FTC Robot Controller code to find your code. You should use @TeleOp to include it under the TeleOp menu on the driver station or **@Autonomous** to include it under the Autonomous menu.

The name parameter sets the name to be included in the menu. Duplicate names are not supported, you should use unique names. If you use the same name on more than one, only one will be included in the menu and you won't know which one.

Finally the **@Disabled** annotation can be used to prevent the robot controller from displaying it in the menu. You can use this feature to create test OpModes that you can enable/disable as you need. The **@Disabled** annotation is commented in this code and so this OpMode will appear in the menu.

These annotations must appear just prior to the class declaration you want them to apply to.

## Class declaration

```
public class LoopTimer1 extends LinearOpMode {
```

This declares a class called LoopTimer1 which extends \(or builds upon\) the LinearOpMode class. The LinearOpMode class is provided by the RobotController and makes the writing of an OpMode easier by creating a structure that we need to follow.

## runOpMode\(\)

```
@Override
public void runOpMode() {
```

This is where we write the code to be run during an OpMode. The RobotConctroller app and the DriverStation app provide for selecting the OpMode and handle the interaction between the DriverStation and the RobotController. When the driver selects Init for an OpMode on the DriverStation, this is the code that runs on the RobotController.

## INIT

```
// (driver presses INIT)
telemetry.addData("Status", "Initialized");
telemetry.addData("Test", "Loop timer using MovingAverageTimer.averageString()");
telemetry.update();

// (driver presses PLAY)
waitForStart();
```

This part is where you initialise any devices and set things up for the run mode. In this case we have no interaction with the robot so there is no hardware initialisation shown here. The code in this example sends some telemetry data from the RobotController app to the DriverStation app. The telemetry variable is provided by the parent class \(LinearOpMode and OpMode\). The Telementry class ensures that updates are sent to the DriverStation with a minimum 250 ms interval between them. Your code can call update more frequently than that but the actual update to the DriverStation will still have an interval of at least 250ms.

The waitForStart\(\) method\(\) pauses the execution of your code until the Start button is pressed on the DriverStation.

## START

We could have created the MovingAverageTimer in the INIT section, but since the time waiting between INIT and START being pressed could be a while, it's easier just to create it here. Also this timer class starts measuring as soon as it is created.

```
// Create a MovingAverageTimer object so that we can time each iteration of the loop
MovingAverageTimer avg = new MovingAverageTimer();
```

The code within this while loop keeps executing until the STOP button is pressed. When the STOP button is pressed the opModeIsActive\(\) becomes false and execution of the while loop is ended.

```
// loop until the end of the match (driver presses STOP)
while (opModeIsActive()) {
```

For each iteration of the loop, the average is updated\(\)

```
// Update and recalculate the average
avg.update();
```

For each iteration of the loop, new telemetry data is scheduled to be sent to the DrvierStation

```
telemetry.addData("Status", avg.averageString());
telemetry.update();
```

It's a good idea to put an idle\(\) call at the end of the loop to ensure that the other parts of the RobotController app and Android Operating System get a chance to do their work too.

```
// Allow other threads their fair share of the CPU
idle();
```

## STOP

When STOP is selected on the driver station, the opModeIsActive\(\) returns false and the while loop exits. This is the end of your OpMode for now. The driver can restart the OpMode by selecting INIT and RUN again without restarting the RobotController.



