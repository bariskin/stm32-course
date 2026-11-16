# Example 01 — GPIO blink / Мигающий светодиод

This folder contains a checklist, not a complete board-specific STM32CubeIDE project.

1. Create a project for your exact STM32F407 device.
2. Configure the LED pin as GPIO Output in CubeMX.
3. Generate code.
4. In the main loop, use the generated pin and port names:

```c
HAL_GPIO_TogglePin(LED_GPIO_Port, LED_Pin);
HAL_Delay(500);
```

`LED_GPIO_Port` and `LED_Pin` are examples of generated/user-defined names; define them for your project or replace them with the actual port and pin. Do not assume a specific LED pin without checking the board schematic.
