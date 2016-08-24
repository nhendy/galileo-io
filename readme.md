# Galileo/Edison/Joule-IO

[![Build Status](https://travis-ci.org/rwaldron/galileo-io.png?branch=master)](https://travis-ci.org/rwaldron/galileo-io)

## Compatible with Intel's Galileo Generation 2 (no longer supports Galileo Generation 1), Edison (Mini and Arduino Board, SparkFun GPIO & Arduino Blocks, Xadow Board, DFRobot Romeo & IO Expansion) and Joule boards.


Galileo/Edison/Joule-IO is a Firmata.js-compatibility class for writing Node.js programs that run on the [Intel Galileo](https://software.intel.com/en-us/iot/hardware/galileo), [Intel Edison](https://software.intel.com/en-us/iot/hardware/edison), or [Intel Joule](https://software.intel.com/en-us/iot/hardware/joule). This project was built at [Bocoup](http://bocoup.com)


## Getting Started

Galileo/Edison/Joule-IO scripts are run directly on the Galileo, Edison or Joule board. To get started, complete the appropriate setup instructions: 

- [Getting Started with the Intel Galileo Board](https://software.intel.com/en-us/get-started-galileo-windows)
- [Get Started with the Intel Edison Development Board](https://software.intel.com/en-us/get-started-edison-windows)
- [Intel Joule Module User Guide
](https://software.intel.com/en-us/intel-joule-getting-started)


### Installation

```
npm install galileo-io johnny-five
```

If you want, you can also use the alias modules: 

For Edison: 

```
npm install edison-io johnny-five
```

For Joule: 

```
npm install joule-io johnny-five
```


But keep in mind that these modules only delegate directly back to this module. 


### Usage

This module is intended for use as an IO-Plugin for [Johnny-Five](https://github.com/rwaldron/johnny-five).

## Pin Identity and Access by Platform


#### Intel Joule (Carrier Board)




The [Intel Joule + Carrier Breakout](https://www.sparkfun.com/products/13097) has two "Breakout connectors": 

[![](joule-breakouts.jpg)](joule-breakouts.jpg)


The usable pins are shown here: 

[![](joule-pins-role-rotated.jpg)](joule-pins-role-rotated.jpg)


Pins may be addressed by their number shown above, or by their "Breakout" name: 


| Breakout Name | Pin Number |
| ------------- | ---------- |
| B1_1 | 1 |
| B1_2 | 2 |
| B1_4 | 4 |
| B1_5 | 5 |
| B1_6 | 6 |
| B1_7 | 7 |
| B1_8 | 8 |
| B1_10 | 10 |
| B1_11 | 11 |
| B1_12 | 12 |
| B1_13 | 13 |
| B1_14 | 14 |
| B1_15 | 15 |
| B1_16 | 16 |
| B1_17 | 17 |
| B1_18 | 18 |
| B1_19 | 19 |
| B1_20 | 20 |
| B1_21 | 21 |
| B1_22 | 22 |
| B1_24 | 24 |
| B1_26 | 26 |
| B1_27 | 27 |
| B1_28 | 28 |
| B1_30 | 30 |
| B1_32 | 32 |
| B1_35 | 35 |
| B2_11 | 51 |
| B2_13 | 53 |
| B2_15 | 55 |
| B2_17 | 57 |
| B2_19 | 59 |
| B2_21 | 61 |
| B2_22 | 62 |
| B2_23 | 63 |
| B2_24 | 64 |
| B2_25 | 65 |
| B2_26 | 66 |
| B2_27 | 67 |
| B2_28 | 68 |
| B2_29 | 69 |
| B2_30 | 70 |
| B2_31 | 71 |
| B2_32 | 72 |
| B2_33 | 73 |
| B2_34 | 74 |
| B2_35 | 75 |
| B2_36 | 76 |
| B2_37 | 77 |
| B2_38 | 78 |
| B2_39 | 79 |
| B2_40 | 80 |
| L1 | 100 |
| L2 | 101 |
| L3 | 102 |
| L4 | 103 |



Additional Pin Capabilities: 

| Pin Number | Capability |
| ---------- | ---------- |
| 7  | UART 0 TX |
| 11 | I2C 0 SDA |
| 13 | I2C 0 SCL |
| 15 | I2C 1 SDA |
| 17 | I2C 1 SCL |
| 19 | I2C 2 SDA |
| 21 | I2C 2 SCL |
| 22 | UART 1 TX |
| 24 | UART 1 RX |
| 26 | PWM0 |
| 28 | PWM1 |
| 30 | PWM2 |
| 32 | PWM3 |
| 68 | UART 0 RX |
| 70 | UART 0 RT |
| 71 | I2C 1 SDA |
| 73 | I2C 1 SCL |
| 74 | UART 1 TX |
| 75 | I2C 2 SDA |
| 76 | UART 1 RX |
| 77 | I2C 1 SCL |


- When using I2C bus 1 or 2, you must explicitly provide that bus to the component being initialized.
- The default I2C bus 0 is assumed when no bus is explicitly provided.



Basic Example: 

```
npm install joule-io johnny-five
```


```js
var five = require("johnny-five");
var Joule = require("joule-io");
var board = new five.Board({
  io: new Joule()
});

board.on("ready", function() {
  var led = new five.Led(103);
  led.blink(500);
});
```



#### Intel Edison Arduino

The [Intel Edison + Arduino Breakout](https://www.sparkfun.com/products/13097) has a pin-out form similar to an Arduino Uno. Use the pin numbers as printed on the board, eg. `3`, `13`, or `"A0"`.

[![](https://cdn.sparkfun.com//assets/parts/1/0/1/3/9/13097-02.jpg)](https://cdn.sparkfun.com//assets/parts/1/0/1/3/9/13097-02.jpg)

Example: 

```
npm install edison-io johnny-five
```


```js
var five = require("johnny-five");
var Edison = require("edison-io");
var board = new five.Board({
  io: new Edison()
});

board.on("ready", function() {
  var led = new five.Led(13);
  led.blink(500);
});
```

#### Intel Edison Mini Breakout

The [Intel Edison + Mini Breakout](https://www.sparkfun.com/products/13025) has a dense pin-out form comprised of four rows, J17, J18, and J19, J20. Each pin is numbered, left-to-right, from 14 to 1 (if looking from the back). Use the row and column name (`"J17-1"`), or the corresponding GPIO (`"GP182"`), or pin number `0`, to interact with that pin. (Note: `"J17-1"`, `"GP182"` and `0` refer to the same pin). See the [table of valid pins](#pin-mapping-table-) below to determine corresponding Pin names and numbers. \*

Connection to bus `1`:

|I2C-1-SDA|I2C-1-SCL|
|---------|---------|
|J17-8    |J18-6    |

[![](https://cdn.sparkfun.com//assets/parts/1/0/0/1/1/13025-01.jpg)](https://cdn.sparkfun.com//assets/parts/1/0/0/1/1/13025-01.jpg)


Example: 

```
npm install edison-io johnny-five
```


```js
var five = require("johnny-five");
var Edison = require("edison-io");
var board = new five.Board({
  io: new Edison()
});

board.on("ready", function() {
  var led = new five.Led("J17-1");
  /*
    Same as: 

    var led = new five.Led(0);
    var led = new five.Led("GP182");
   */
  led.blink(500);
});
```


#### SparkFun Edison GPIO Block

The [SparkFun Edison GPIO Block](https://www.sparkfun.com/products/13038) has two columns of pins. Use the GPIO name printed on the board (`"GP44"`), or the corresponding row and column name (`"J19-4"`), or pin number (`31`), to interact with that pin. (Note: `"J19-4"`, `"GP44"` and `31` refer to the same pin). See the [table of valid pins](#pin-mapping-table-) below to determine corresponding Pin names and numbers. \*

[![](https://cdn.sparkfun.com//assets/parts/1/0/0/3/9/13038-03.jpg)](https://cdn.sparkfun.com//assets/parts/1/0/0/3/9/13038-03.jpg)

Example: 

```
npm install edison-io johnny-five
```


```js
var five = require("johnny-five");
var Edison = require("edison-io");
var board = new five.Board({
  io: new Edison()
});

board.on("ready", function() {
  var led = new five.Led("GP44");
  /*
    Same as: 

    var led = new five.Led(31);
    var led = new five.Led("J19-4");
   */
  led.blink(500);
});
```

#### SparkFun Edison Arduino Block

The [SparkFun Edison Arduino Block](https://www.sparkfun.com/products/13046) connects to the Edison via `Serial1`, or `/dev/ttyMFD1`. This means that a user must [upload StandardFirmata via FTDI programmer](https://learn.sparkfun.com/tutorials/sparkfun-blocks-for-intel-edison---arduino-block). Johnny-Five does not use Galileo/Edison/Joule-IO to communicate with the hardware on this block, instead it communicates via the serial connection, using its default [`Firmata.js`](https://github.com/jgautier/firmata) (this is installed by Johnny-Five automattically. The port name must be specified: 

```js
// This code runs on the Edison, communicating with the 
// SparkFun Arduino Block via Serial1 (/dev/ttyMFD1)
var five = require("johnny-five");
var board = new five.Board({
  port: "/dev/ttyMFD1"
});

board.on("ready", function() {
  var led = new five.Led(13);
  led.blink(500);
});
```

[![](https://cdn.sparkfun.com//assets/parts/1/0/0/3/7/13036-01.jpg)](https://cdn.sparkfun.com//assets/parts/1/0/0/3/7/13036-01.jpg)


#### SparkFun Edison I2C Block

Galileo/Edison/Joule-IO/Edison-IO will automatically connect to bus 1, which is the bus used by this block.


#### SparkFun Edison 9DOF Block

Galileo/Edison/Joule-IO/Edison-IO will automatically connect to bus 1, which is the bus used by this block.




#### Edison Mini Pin Mapping Table \* 

| Pin Number  | Physical Pin | Edison Pin    |
|-------------|--------------|---------------|
| 0           | J17-1        | GP182         |
| 4           | J17-5        | GP135         |
| 6           | J17-7        | GP27          |
| 7           | J17-8        | GP20          |
| 8           | J17-9        | GP28          |
| 9           | J17-10       | GP111         |
| 10          | J17-11       | GP109         |
| 11          | J17-12       | GP115         |
| 13          | J17-14       | GP128         |
| 14          | J18-1        | GP13          |
| 15          | J18-2        | GP165         |
| 19          | J18-6        | GP19          |
| 20          | J18-7        | GP12          |
| 21          | J18-8        | GP183         |
| 23          | J18-10       | GP110         |
| 24          | J18-11       | GP114         |
| 25          | J18-12       | GP129         |
| 26          | J18-13       | GP130         |
| 31          | J19-4        | GP44          |
| 32          | J19-5        | GP46          |
| 33          | J19-6        | GP48          |
| 35          | J19-8        | GP131         |
| 36          | J19-9        | GP14          |
| 37          | J19-10       | GP40          |
| 38          | J19-11       | GP43          |
| 39          | J19-12       | GP77          |
| 40          | J19-13       | GP82          |
| 41          | J19-14       | GP83          |
| 45          | J20-4        | GP45          |
| 46          | J20-5        | GP47          |
| 47          | J20-6        | GP49          |
| 48          | J20-7        | GP15          |
| 49          | J20-8        | GP84          |
| 50          | J20-9        | GP42          |
| 51          | J20-10       | GP41          |
| 52          | J20-11       | GP78          |
| 53          | J20-12       | GP79          |
| 54          | J20-13       | GP80          |
| 55          | J20-14       | GP81          |


#### Intel Galileo Gen 2

> Or Gen 1 if you're a glutton for punishment. 

The [Intel Galileo Gen 2](https://www-ssl.intel.com/content/www/us/en/do-it-yourself/galileo-maker-quark-board.html) has a pin-out form similar to an Arduino Uno. Use the pin numbers as printed on the board, eg. `3`, `13`, or `"A0"`.

[![](https://cdn.sparkfun.com//assets/parts/1/0/1/3/8/13096-01.jpg)](https://cdn.sparkfun.com//assets/parts/1/0/1/3/8/13096-01.jpg)

Example: 

```js
var five = require("johnny-five");
var Galileo = require("galileo-io");
var board = new five.Board({
  io: new Galileo()
});

board.on("ready", function() {
  var led = new five.Led(13);
  led.blink(500);
});
```






### Blink an Led

The "Hello World" of microcontroller programming:

(attach an LED on pin 9)

```js
var Galileo = require("galileo-io");
var board = new Galileo();

board.on("ready", function() {
  var byte = 0;
  this.pinMode(9, this.MODES.OUTPUT);

  setInterval(function() {
    board.digitalWrite(9, (byte ^= 1));
  }, 500);
});
```

### Johnny-Five IO Plugin

Galileo/Edison/Joule-IO is the default [IO layer](https://github.com/rwaldron/johnny-five/wiki/IO-Plugins) for [Johnny-Five](https://github.com/rwaldron/johnny-five) programs that are run on a Galileo or Edison board.

***Note:*** On the Edison, you should require johnny-five first, followed by galileo-io. Otherwise you'll get a segmentation fault.


```
npm install edison-io johnny-five
```

Example:
```js
var five = require("johnny-five");
var Edison = require("edison-io");
var board = new five.Board({
  io: new Edison()
});
```

### Specify An I2C Bus

Galileo/Edison/Joule-IO will do it's best to detect the correct I2C bus to use for a given expansion board, however the process is not infallible. To specify an I2C bus: 

```js
// If the i2c bus is 1 (`/dev/i2c-1`)
var board = new Galileo({
  i2c: {
    bus: 1
  }
});
```

Or...

```js
var board = new Edison({
  i2c: {
    bus: 1
  }
});
```

#### Xadow Board

Expansion boards can also be initialized with a built-in configuration object, that contains the correct I2C bus for that board: 


```
npm install edison-io johnny-five
```

Example:
```js
var five = require("johnny-five");
var Edison = require("edison-io");
var board = new five.Board({
  io: new Edison(Edison.Boards.Xadow)
});
```

Or 

```js
var five = require("johnny-five");
var Galileo = require("galileo-io");
var board = new five.Board({
  io: new Galileo(Galileo.Boards.Xadow)
});
```

**Additional expansion board configurations will be added as support is implemented**


### API

**digitalWrite(pin, 1|0)**

> Sets the pin to 1 or 0, which either connects it to 5V (the maximum voltage of the system) or to GND (ground).

Example:
```js
// This will turn on the pin
board.digitalWrite(9, 1);
```



**analogWrite(pin, value)**

> Sets the pin to a value between 0 and 255, where 0 is the same as LOW and 255 is the same as HIGH. This is sort of like sending a voltage between 0 and 5V, but since this is a digital system, it uses a mechanism called Pulse Width Modulation, or PWM. You could use analogWrite to dim an LED, as an example.

Example:
```js
// Crank an LED to full brightness
board.analogWrite(9, 255);
```

**servoWrite(pin, value)** 

> Set the pin to a value between 0-180° to move the servo's horn to the corresponding position.

Example:
```js
board.servoWrite(9, 180);
```

**digitalRead(pin, handler)** Setup a continuous read handler for specific digital pin.

> This will read the digital value of a pin, which can be read as either HIGH or LOW. If you were to connect the pin to 5V, it would read HIGH (1); if you connect it to GND, it would read LOW (0). Anywhere in between, it’ll probably read whichever one it’s closer to, but it gets dicey in the middle.

Example:
```js
// Log all the readings for 9
board.digitalRead(9, function(data) {
  console.log(data);
});
```


**analogRead(pin, handler)** Setup a continuous read handler for specific analog pin.

> This will read the analog value of a pin, which is a value from 0 to 4095, where 0 is LOW (GND) and 4095 is HIGH (5V). All of the analog pins (A0 to A5) can handle this. analogRead is great for reading data from sensors.


Example:
```js
// Log all the readings for A1
board.analogRead("A1", function(data) {
  console.log(data);
});

```

## License
See LICENSE file.

