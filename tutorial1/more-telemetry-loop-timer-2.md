# More Telemetry - Loop Timer 2

The Loop Timer 1 OpMode displayed a simple string showing the average loop time. However the MovingAverage class can display a lot more information than that. The Loop Timer 2 OpMode uses the MovingAverage .toString\(\) method to display more information. 

```
            telemetry.addData("Status", avg.toString());
```

If you re-reun the RobotController you should see something like the picture below

![](/assets/LoopTimer2.png)

This display now shows a lot more information. It shows a loop counter, total time, moving average and a simple average. It also shows min and max values for loop time, moving average and simple average respectively.

If you watch the display you can see the loop counter incrementing in large increments. This is because the Telemetry class only sends updates to the Driver Station every 250ms, not every loop. Also note the variance in the loop time. The maximum loop time was 13.91 milliseconds quite a bit more than the average.

Also note that the average loop time is quite a bit more than for Loop Timer 1. The average is now 0.496 milliseconds per loop and an equivalent 2,000 loops per second. Quite a bit slower.

