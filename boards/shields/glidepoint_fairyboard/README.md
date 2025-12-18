# Glidepoint for fairyboard

This shield is used to connect a cirque glidepoint trackpad to a fairyboard.

To use this shield, you should have an I2C1 interface in your device tree and access to pins D0 and D4 on your pro-micro equivalent.

The glidepoint trackpad will use the D0 pin (P0.08 on nice!nano) for SDA and D4 pin (P0.22 of nice!nano) for SCL with the glidepoint set to I2C mode. You may have to remove a resistor to put the trackpad in this mode. This references `i2c1` as `glidepoint_i2c` and exposes `glidepoint` which can be used within an input listener, i.e.

```dts
/{
    glidepoint_input: glidepoint_input {
        compatible = "zmk,input-listener";
        device = <&glidepoint>;
    };
};
```

You can build with

```sh
west build -b nice_nano_v2 -- -DSHIELD="fairyboard glidepoint_fairyboard"
```
