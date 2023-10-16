Answers to homework questions:
Board: STM32L152C Discovery Board
Button: B1 (B1_Pin == PA0)
LED: LD4 (PB6)

When the button is pressed (GPIOA->IDR & GPIO_PIN_0 == GPIO_PIN_SET), the ***external interrupt*** (EXT0_IRQn) is triggered and the LED is toggled through the GPIOB->BSRR register.
The value of the input register (button) can be read through GPIOA->IDR, which is a read-only register.
The value of the output register (LED) can be read and written to the GPIOB->ODR or GPIOB->BSRR registers. 
The advantage of using the BSRR register is that the ODR register value can be changed atomically (single-instruction cycle, so no interrupt when BSRR register is being set)


