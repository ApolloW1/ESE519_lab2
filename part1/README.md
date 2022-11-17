# Part 1
The direct register reads to access the boot button status is acheived by code below:

```
boot_pin_address = (volatile uint32_t *) 0xd0000004; // the pointer of boot_pin_address
full_gpio_register_value = (uint32_t) *boot_pin_address; // retrive the register value lies in the address
pin_21_selection_mask = 1u << 21; // mask used to retrieve the 21st bit
selected_pin_state = full_gpio_register_value & pin_21_selection_mask; 
shifted_pin_21_state = selected_pin_state >> 21;// retrive the bit value
```

LED will be toggled when the button is pressed.
