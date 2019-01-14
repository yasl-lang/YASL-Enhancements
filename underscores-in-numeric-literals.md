# Underscores in Numeric Literals
Integers and floats should allow embedded underscores for readability.

The following are allowed:
* 1_000_000
* 1_000_
* 1____000
* 100.000_00
* 1.0__
* 1_0.01_0
* 0b1000_1011
* 0xCAFE_BABE
* 0b_1001_1010
* 0x_10_AB

The following are not:
* _0x10
* _0b10
* 0_x10
* _10
* 1._9
