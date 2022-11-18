# Part 8
The sequencer is used for controlling the sensor with implementation of ADPS9960 protocol.

'''

    void APDS9960_init(PIO pio, uint sm,uint8_t addr, bool nostop) {

    // initialize the APDS9960 based on the datasheet
        int len = 2;
        uint8_t config[2];
        config[0] = ENABLE_REG;
        config[1] = INIT_CONFIG;
        pio_i2c_write_blocking(pio, sm, addr, config, len, false);
        config[0] = ALS_TIME_REG;
        config[1] = ALS_TIME;
        pio_i2c_write_blocking(pio, sm, addr, config, len, false);
    }
'''
