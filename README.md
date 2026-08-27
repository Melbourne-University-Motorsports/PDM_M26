# PDM_M26

> Fan 1 and 2 need to be changed to Timer pins in stm32cubeMX

Testing code for M26 PDM with a STM32 Nucleo32 G431KB.
*Haven't done any CAN firmware yet*

Build with CMake and then use the Flash Task to flash the board. Run a live debug session. Use Serial monitor to open an SWO:ITM terminal for the ST-link connection (Idk if thats how ur supposed to do it but it works) and you should see the readings print.

Overcurrent limit for 3 High side switches (Fan 1, 2, HighCurrent) is set to 7A, 
Pump out is limited to 4A because it is fused for 5A

### Pinouts
---
| NUMBER | PIN | TYPE | MODE | PINOUT | DIRECTION | FUNCTION | REQUIREMENT |
|---|---|---|---|---|---|---|---|
| PA9 | D1 | | | | | | |
| PA10 | D0 | Digital | | STB | OUT | STB | |
| RST_CN4 | NRST | | | | | | |
| GND_CN4 | GND | Power | NA | Ground | | | |
| PA12 | D2 | Digital | FDCAN1_TX | CAN_TX | OUT | CAN transmit | |
| PB0 | D3 | Digital | GPIO | Fan 1 Diagnostics | IN | Diagnostic Enable | |
| PB7 | D4 | Timer/Dig | TIM4_CH2 | Fan 1 Enable | OUT | PWM | 20KHz, 0-100% |
| PA15 | D5 | Timer/Dig | TIM2_CH1/GPIO | Pump Enable | OUT | ON/OFF | OFF = LOW, ON = HIGH |
| PB6 | D6 | Digital | GPIO | Pump Diagnostics | IN | Diagnostic Enable | OFF = DISABLED, ON = ENABLED |
| PF0 | D7 | | | | | | |
| PF1 | D8 | Digital | GPIO | High Current Diagnostics | IN | Diagnostic Enable | |
| PA8 | D9 | Timer/Dig | TIM1_CH1 | Fan 2 Enable | OUT | PWM | 20KHz, 0-100% |
| PA11 | D10 | Digital | FDCAN1_RX | CAN_RX | IN | CAN receive | |
| PB5 | D11 | Digital | GPIO | Fan 2 Diagnostics | IN | Diagnostic Enable | OFF = DISABLED, ON = ENABLED |
| PB4 | D12 | Timer/Dig | TIM3_CH1/GPIO | High Current Enable | OUT | ON/OFF | OFF = LOW, ON = HIGH |
| | | | | | | | |
| VIN | VIN | | | | | | |
| GND_CN3 | GND | Power | NA | Ground | | | |
| RST_CN3 | NRST | | | | | | |
| 5V | 5V | | | | | | |
| PA2 | A7 | Analog | GPIO_Analog | Fan 2 Sense | IN | ADC | I = V_ADC / 0.308 |
| PA7 | A6 | Analog | GPIO_Analog | High Current Sense | IN | ADC | I = V_ADC / 0.308 |
| PA6 | A5 | Analog | GPIO_Analog | Fan 1 Sense | IN | ADC | I = V_ADC / 0.308 |
| PA5 | A4 | Analog | GPIO_Analog | Low Current Sense 2 | IN | ADC | I = V_ADC / 0.5999 |
| PA4 | A3 | Analog | GPIO_Analog | Low Current Sense 1 | IN | ADC | I = V_ADC / 0.5999 |
| PA3 | A2 | | | | | | |
| PA1 | A1 | Analog | GPIO_Analog | Pump Sense | IN | ADC | I = V_ADC / 0.308 |
| PA0 | A0 | Analog | GPIO_Analog | Battery Reference | IN | ADC | |
| AREF | AVDD | | | | | | |
| 3V3 | 3V3 | Power | NA | 3.3V Bus | | | |
| PB3/PB8 | D13 | | | | | | |
