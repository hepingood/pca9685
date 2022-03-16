[English](/README.md) | [ 简体中文](/README_zh-Hans.md) | [繁體中文](/README_zh-Hant.md)

<div align=center>
<img src="/doc/image/logo.png"/>
</div>

## LibDriver PCA9685

[![API](https://img.shields.io/badge/api-reference-blue)](https://www.libdriver.com/docs/pca9685/index.html) [![License](https://img.shields.io/badge/license-MIT-brightgreen.svg)](/LICENSE)

The PCA9685 is an I2C-bus controlled 16-channel LED controller optimized for Red/Green/Blue/Amber (RGBA) color backlighting applications. Each LED output has its own 12-bit resolution (4096 steps) fixed frequency individual PWM controller that operates
at a programmable frequency from a typical of 24 Hz to 1526 Hz with a duty cycle that is adjustable from 0 % to 100 % to allow the LED to be set to a specific brightness value.All outputs are set to the same PWM frequency.Each LED output can be off or on (no PWM control), or set at its individual PWM controller value. The LED output driver is programmed to be either open-drain with a 25 mA current sink capability at 5 V or totem pole with a 25 mA sink, 10 mA source capability at 5 V. The PCA9685 operates with a supply voltage range of 2.3 V to 5.5 V and the inputs and outputs are 5.5 V tolerant. LEDs can be directly connected to the LED output (up to 25 mA, 5.5 V) or controlled with external drivers and a minimum amount of discrete components for larger current or higher voltage LEDs.It can be used in RGB or RGBA LED drivers, LED status information, LED displays, LCD backlights, Keypad backlights for cellular phones or handheld devices and so on.

LibDriver PCA9685 is the full function driver of PCA9685 launched by LibDriver.PCA9685 provides pwm output and other functions.

### Table of Contents

  - [Instruction](#Instruction)
  - [Install](#Install)
  - [Usage](#Usage)
    - [example basic](#example-basic)
  - [Document](#Document)
  - [Contributing](#Contributing)
  - [License](#License)
  - [Contact Us](#Contact-Us)

### Instruction

/src includes LibDriver PCA9685 source files.

/interface includes LibDriver PCA9685 IIC platform independent template。

/test includes LibDriver PCA9685 driver test code and this code can test the chip necessary function simply。

/example includes LibDriver PCA9685 sample code.

/doc includes LibDriver PCA9685 offline document.

/datasheet includes PCA9685 datasheet。

/project includes the common Linux and MCU development board sample code. All projects use the shell script to debug the driver and the detail instruction can be found in each project's README.md.

### Install

Reference /interface IIC platform independent template and finish your platform IIC driver.

Add /src, /interface and /example to your project.

### Usage

#### example basic

```C
volatile uint8_t res;
volatile uint32_t i, times;
pca9685_address_t address;
pca9685_channel_t channel;

address = PCA9685_ADDRESS_A000000;
channel = PCA9685_CHANNEL_0;
times = 10;

res = pca9685_basic_init(address, 50);
if (res)
{
    return 1;
}

...

for (i = 1; i < times + 1; i++)
{
    res = pca9685_basic_write(channel, 0.0f, 2.5f + (float)(i) / (float)(times) * 10.0f);
    if (res)
    {
        pca9685_basic_deinit();

        return 1;
    }

    pca9685_interface_debug_print("pca9685: set channel %d %0.2f degrees.\n", channel, (float)(i) / (float)(times) * 180.0f);

    pca9685_interface_delay_ms(1000);
    
    ...
}

...

pca9685_basic_deinit();

return 0;
```

### Document

Online documents: https://www.libdriver.com/docs/pca9685/index.html

Offline documents: /doc/html/index.html

### Contributing

Please sent an e-mail to lishifenging@outlook.com

### License

Copyright (c) 2015 - present LibDriver All rights reserved



The MIT License (MIT) 



Permission is hereby granted, free of charge, to any person obtaining a copy

of this software and associated documentation files (the "Software"), to deal

in the Software without restriction, including without limitation the rights

to use, copy, modify, merge, publish, distribute, sublicense, and/or sell

copies of the Software, and to permit persons to whom the Software is

furnished to do so, subject to the following conditions: 



The above copyright notice and this permission notice shall be included in all

copies or substantial portions of the Software. 



THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR

IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,

FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE

AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER

LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,

OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE

SOFTWARE. 

### Contact Us

Please sent an e-mail to lishifenging@outlook.com