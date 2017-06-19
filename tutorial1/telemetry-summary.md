# Telemetry Summary

The table below summarises the telemetry results we observed for the Three OpModes:

| OpMode | Average Loop Time \(msecs\) | Loops per seconds |
| :--- | :--- | :--- |
| Loop Timer 1 | 0.089 | 11,000 |
| Loop Timer 2 | 0.496 | 2,000 |
| Loop Timer 3 | 0.016 | 62,000 |

Loop Timer 1 and Loop Timer 2 use the same method for updating the telemetry. The only difference is that Loop Timer 2 is generating a larger and more complex string. String operations are more expensive in terms of CPU than simple numeric math operations and so that is the main difference.

Loop Timer 3 displays the same information as Loop Timer 1 but is significantly faster. This again is likely due to String operations. The Telemetry class only updates the Driver Station 4 times a second, but Loop Timer 1 is generating a String representation of the number for every loop. Loop Timer 3 on the other hand is recording the number every loop, but only generating the string when it updates.

In summary,  for better performance, use Telemetry.Item to update values rather than Telemetry.addData\(\).

