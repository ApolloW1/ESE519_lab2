# Part 8
The sequencer is used for reading the sensor with implementation of ADPS9960 protocol.

The initialization is achieved by function below:

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
    
Read Function:

    void read_value(int32_t* red, int32_t* green, int32_t* blue, int32_t* clear, int32_t* prox, PIO pio, uint sm, uint8_t addr, bool nostop) {

        uint8_t buf[1];
        uint8_t reg = PDATA_REG;
        pio_i2c_write_blocking(pio, sm, addr, &reg, 1, nostop);  
        pio_i2c_read_blocking(pio, sm, addr, buf, 1); 

        *prox = buf[0];

        uint8_t buffer[2];
        reg = CDATA_REG_L;
        pio_i2c_write_blocking(pio, sm, addr, &reg, 1, nostop);  
        pio_i2c_read_blocking(pio, sm, addr, buffer, 8); 

        *clear = (buffer[1] << 8) | buffer[0];
        *red = (buffer[3] << 8) | buffer[2];
        *green = (buffer[5] << 8) | buffer[4];
        *blue = (buffer[7] << 8) | buffer[6];

    }

## Result
<img width="449" alt="截屏2022-11-18 下午5 49 14" src="https://user-images.githubusercontent.com/114015725/202816030-aacb0f16-4232-4556-a942-0229d0391c59.png">
