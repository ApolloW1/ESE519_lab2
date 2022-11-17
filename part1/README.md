# Part 1
The direct register reads to access the boot button status is acheived by code below:

```
boot_pin_address = (volatile uint32_t *) 0xd0000004;

full_gpio_register_value = (uint32_t) *boot_pin_address; 

pin_21_selection_mask = 1u << 21; 

selected_pin_state = full_gpio_register_value & pin_21_selection_mask; 

shifted_pin_21_state = selected_pin_state >> 21;
```

LED will be toggled when the button is pressed.
