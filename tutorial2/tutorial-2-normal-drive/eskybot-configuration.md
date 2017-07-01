# EskyBot Configuration

We are going to create an EskyBot configuration by copying the TwoMotorRobot configuration in the FGCExamples project. We will use the EskyBot configuration to store references to the motor objects. We can then create multiple OpModes using the 

## Create the configurations package

First we need to create a new package directory to hold our configurations. Java uses packages to logically separate code. Right click on the org.baconeers package in the TeamCode project and selct New\|Package

![](/assets/tut2_new_package.png)

Then enter "configurations" and click OK.

![](/assets/tut2_new_package_configurations.png)

## Copy an existing configuration

Rather than create a new configuration from scratch, we will copy an existing one from the FGCExamples project. Locate the TwoMotorRobot class in the FGCExamples. 

![](/assets/tut2project2_TwoMotorRobot.png)

Select the TwoMotorRobot with the left mouse button, and then with the CTRL key held down, drag it using the left mouse button to the new configurations package you just created. The plus sign when you drag indicates a copy, without the CTRL key, the plus sign is not shown and that indicates a move. Keep the CTRL key down until after you release the left mouse button. You will then be presented with a dialog box to copy the class.

![](/assets/tut2_new_package_copy_two_motor_robot.png)

Rename the TwoMotorRobot to EskyBot and click OK

![](/assets/tut2_new_package_copy_eskybot.png)

Android studio has renamed the class, but didn't rename the static factory method in the class

![](/assets/tut2_new_package_copy_eskybot_fix_errors.png)

Fix this by changing TwoMotorRobot to EskyBot in the code section above.

![](/assets/tut2_new_package_copy_eskybot_fixed.png)

