| Supported Targets | ESP32 | ESP32-C6 | ESP32-H2 | ESP32-P4 | ESP32-S3 |
| ----------------- | ----- | -------- | -------- | -------- | -------- |
# MCPWM RC Servo Control Example

This prject was created from the "ESP-IDF: Explorer" -> "New Project Wizard" for the
ESP32-S3 microcontroller using the "MCPWM RC Servo Control Example" template.

It is an example that illustrates how to drive a typical [RC Servo](https://en.wikipedia.org/wiki/Servo_%28radio_control%29) by sending a PWM signal using the MCPWM driver. The PWM pulse has a frequency of 50Hz (period of 20ms), and the active-high time (which controls the rotation) ranges from 0.5s to 2.5ms with 1.5ms always being center of range.

## How to Use Example

### Hardware Required

* A LILYGO T-Display-S3 ESP32-S3 1.9 inch ST7789 LCD Display TTGO Development Board (https://www.amazon.co.uk/dp/B09J112YR7) development board,
* A USB cable for Power supply and programming, and
* A RC servo motor, e.g. [SG90](http://www.ee.ic.ac.uk/pcheung/teaching/DE1_EE/stores/sg90_datasheet.pdf) or an [FS90R](https://www.amazon.co.uk/gp/product/B09K74X3MZ).

Personally I think the FS90R is the better test option as, being a continual rotating device
is is easier to see when working. An SG90 move is relativily small increments, so needsd more 
careful observation.

Connection :

```
 T-Display-S3             Servo Motor
+------------+         +-------------+
|        VCC +-- 5v  --+ VCC (Red)   +
|            |         |             |
|        GND +-- GND --| GND(Brown)  |
|            |         |             |
|         NC |         |             |
|            |         |             |
|         NC |         |             |
|            |         |             |
|    GPIO 13 +-----+ PWM (Yellow)    |
|            |         |             |
|            |         |             |
|            |         |             |
+------------+         +-------------+
```

Note that, some kind of servo might need a higher current supply than the development board usually can provide. It's recommended to power the servo separately.

### Build and Flash

Run `idf.py -p PORT flash monitor` to build, flash and monitor the project.

(To exit the serial monitor, type ``Ctrl-]``.)

See the [Getting Started Guide](https://docs.espressif.com/projects/esp-idf/en/latest/get-started/index.html) for full steps to configure and use ESP-IDF to build projects.


## Example Output

Run the example, you will see the following output log:

```
...
I (0) cpu_start: Starting scheduler on APP CPU.
I (305) example: Create timer and operator
I (305) example: Connect timer and operator
I (305) example: Create comparator and generator from the operator
I (315) gpio: GPIO[44]| InputEn: 0| OutputEn: 1| OpenDrain: 0| Pullup: 1| Pulldown: 0| Intr:0
I (325) example: Set generator action on timer and compare event
I (335) example: Enable and start timer
I (335) example: Angle of rotation: 0
I (1345) example: Angle of rotation: 2
I (2345) example: Angle of rotation: 4
I (3345) example: Angle of rotation: 6
I (4345) example: Angle of rotation: 8
I (5345) example: Angle of rotation: 10
I (6345) example: Angle of rotation: 12
I (7345) example: Angle of rotation: 14
I (8345) example: Angle of rotation: 16
I (9345) example: Angle of rotation: 18
...
```

An SG90 servo will rotate from -90 degree to 90 degree, and then turn back again. An FG90R
servo will first rotate anti-clockwise direction and then clockwise before repeating. 

## Troubleshooting

For any technical queries, please open an [issue] (https://github.com/espressif/esp-idf/issues) on GitHub. We will get back to you soon.
