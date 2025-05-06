# **API**

## **User ID Assignments**

| User | User ID |
| ----- | ----- |
| **Aadish** | **A** |
| Shaurya | S |

## **Message Structure**

| Byte \# | Field Name | Data Type | Description |
| ----- | ----- | ----- | ----- |
| 1-2 | **Prefix** | `uint16_t` | Message start identifier |
| 3 | **Sender ID** | `uint8_t` | Identifies who sent the message |
| 4 | **Receiver ID** | `uint8_t` | Identifies who should receive the message |
| 5-6 | **Data** | `uint16_t` | Message-specific data |
| 7-8 | **Suffix** | `uint16_t` | Message end identifier |

## **Messages My Subsystem Sends & Receives**

### **Message Type 1 – Motor Direction Command**

| Byte | Variable Name | Data Type | Min Value | Max Value | Example |
| ----- | ----- | ----- | ----- | ----- | ----- |
| 1-2 | `prefix` | `uint16_t` | 0x0001 | 0x0001 | 0x0001 |
| 3 | `sender_id` | `uint8_t` | 0xFF | 0xFF | 0xFF |
| 4 | `receiver_id` | `uint8_t` | 0xFD | 0xFD | 0xFD |
| 5-6 | `motor_direction` | `uint16_t` | 0x40 (Forward) | 0x41 (Reverse) | 0x40 |
| 7-8 | `suffix` | `uint16_t` | 0x0020 | 0x0020 | 0x0020 |

**Function:** Commands Aadish to change motor direction.

### **Message Type 2 – Acknowledgement**

| Byte | Variable Name | Data Type | Min Value | Max Value | Example |
| ----- | ----- | ----- | ----- | ----- | ----- |
| 1-2 | `prefix` | `uint16_t` | 0x0002 | 0x0002 | 0x0002 |
| 3 | `sender_id` | `uint8_t` | 0xFC | 0xFC | 0xFC |
| 4 | `receiver_id` | `uint8_t` | 0xFD | 0xFD | 0xFD |
| 5-6 | `motor_speed` | `uint16_t` | 0x42 (Increase) | 0x43 (Decrease) | 0x42 |
| 7-8 | `suffix` | `uint16_t` | 0x0021 | 0x0021 | 0x0021 |

**Function:** Updates the motor speed in Aadish’s motor driver system.

## **Message Handling Code**

#include "mcc_generated_files/mcc.h"
#include "mcc_generated_files/spi1.h"

#define MY_ID 'A'

#define FWD_CMD 0b11101111
#define REV_CMD 0b11101101
#define OFF_CMD 0b11100000

void send_uart_message(const char* msg) {
    for (uint8_t i = 0; i < 8; i++) {
        while (!EUSART1_is_tx_ready());
        EUSART1_Write(msg[i]);
    }
}

void send_confirmation(char action) {
    char msg[8] = { 'F', 'S', 'A', 'S', '0', action, 'F', 'S' };
    send_uart_message(msg);
}


void main(void) 
{

    SYSTEM_Initialize();
    SPI1_Open(SPI1_DEFAULT);
    CS_SetHigh();
    __delay_ms(500);
    
    char rx_buf[8] = {0};

    while (1)
    {
        if (EUSART1_is_rx_ready()) {
            char byte = EUSART1_Read();

            for (uint8_t i = 0; i < 7; i++) rx_buf[i] = rx_buf[i + 1];
            rx_buf[7] = byte;

            if (rx_buf[0] == 'F' && rx_buf[1] == 'S' &&
                rx_buf[2] == 'S' && rx_buf[3] == 'A' &&
                rx_buf[4] == '0' && rx_buf[6] == 'F' && rx_buf[7] == 'S') {

                char cmd = rx_buf[5];

                if (cmd == '1') {
                    CS_SetLow(); SPI1_ExchangeByte(FWD_CMD); CS_SetHigh();
                } else if (cmd == '2') {
                    CS_SetLow(); SPI1_ExchangeByte(REV_CMD); CS_SetHigh();
                } else if (cmd == '3') {
                    CS_SetLow(); SPI1_ExchangeByte(OFF_CMD); CS_SetHigh();
                }

                send_confirmation(cmd); // Send reply to S
            }
        }
    }
}
