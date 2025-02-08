---
title: Individual Component Selection
---

EGR 314: Aadish Lele Team 309
Professor Nichols

Microcontroller Selection:

Requirements:
I2C communication protocol for sending data from the motor driver to the ESP32 and multiple GPIO pins of the PIC DIP microcontroller.

Microcontroller Considerations:
PIC18F27Q10

| PIC Info                                      | Answer                                    |       
| --------------------------------------------- | ------------------------------------------| 
| Model                                         | PIC18F27Q10                                                  |   
| Product Page URL                              | [link](https://www.microchip.com/en-us/product/PIC18F27Q10)  |                                       
| Datasheet URL(s)                              | [link](#https://ww1.microchip.com/downloads/aemDocuments/documents/MCU08/ProductDocuments/DataSheets/PIC18F27-47Q10-Micorcontroller-Data-Sheet-DS40002043.pdf)       | Application Notes URL(s)                      | [link](#https://www.microchip.com/en-us/application-notes/tb3237)|                                        
| Vendor link                                   | [link](#https://www.microchip.com/)                              | 
| Code Examples                                 | [link](#https://github.com/mojulian/BME280_Interface_for_PIC18F/blob/master/BME280.c) |
| External Resources URL(s)                     | [link](#https://www.arrow.com/en/products/pic18f27q10-estx/microchip-technology)     | 
| Unit cost                                     | $1.05                        |                                                       
| Absolute Maximum Current for entire IC        | 10 A                         |                                                               
| Supply Voltage Range                          | 1.8V - 5.5V                  |                                                                          
| Maximum GPIO current <br> (per pin)           | 10 nA                        | 
| Supports External Interrupts?                 | Yes                          | 
| Required Programming Hardware, Cost, URL      | None                         | 
| Works with MPLabX?                            | Yes                          | 
| Works with Microchip Code Configurator?       | Yes [image](#             |

Pins Table
| Module     | # Available | Needed | Associated Pins (or * for any) |
| ---------- | ----------- | ------ | ------------------------------ |
| GPIO       | 12          | 4`     | Any GPIO Pin                   |
| ADC        | 2           | 2      | Any ADC Pin                    |
| UART       | 6           | 1      | Any UART Pin                   |
| SPI        | 2           | 1      | Any SPI Pin                    |
| I2C        | 2           | 1      | Any I2C Pin                    |
| PWM        | 2           | 1      | Any PWM Pin                    |
| ICSP       | 2           | 0      | Any GPIO Pin                   |
| ...        | ...         | ...    | ...                            |


Role Description:
My role in the team is to program and design a motor driver and the motor which is the heart of our project. Our project is basically a spinning top with a HMI that will be able to control speed and direction of our spinning top. I will be using the PIC to ensure that when data and power are supplied, it runs and is able to balance itself on the ground. For this it is very essential for me to get the speed and direction of the motor right as that will smoothen the further process of sending that data to the ESP32 module. I am responsible for actuation using the motor and the motor driver.


*Screenshots of MCC using the selected PIC

Microcontroller Rationale:
The PIC18F27Q10 is an excellent choice for our spinning top project because of its high-performance 8-bit architecture and varied peripherals. It uses
efficient motor control With PWM modules and can use the Adafruit motor for its precise control.It also uses low power consumption and can help saving power for other subsytems. It also includes UART/SPi/I2C communication protocols and interfaces for interacting with the motor and motor driver. It supports ADC fro impementing Gyroscopes for motion control and balace which is another subsytem of our project. These features make the PIC18F27Q10 a power-efficient, and scalable microcontroller for ensuring smooth operation and precise control with PWMs.

