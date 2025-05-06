# **Application Programming Interface**

## **User ID Assignments**

| User | User ID |
| ----- | ----- |
| **Aadish** | **0xFD** |
| Shaurya | 0xFC |

## **Message Structure**

| Byte \# | Field Name | Data Type | Description |
| ----- | ----- | ----- | ----- |
| 1-2 | **Prefix** | `uint16_t` | Message start identifier |
| 3 | **Sender ID** | `uint8_t` | Identifies who sent the message |
| 4 | **Receiver ID** | `uint8_t` | Identifies who should receive the message |
| 5-6 | **Data** | `uint16_t` | Message-specific data |
| 7-8 | **Suffix** | `uint16_t` | Message end identifier |

## **Message Types**

### **Message Type 1 – Motor Direction Command (Sent from Shaurya to Aadish) **

| Condition           | Message ID | Meaning        |
|---------------------|------------|----------------|
| Temp ≤ 25°C         | 0x01       | Motor Forward  |
| 25°C < Temp ≤ 30°C  | 0x02       | Motor Reverse  |
| Temp > 30°C         | 0x03       | Motor Off      |

**Function:** Commands Aadish to change motor direction.

### **Message Type 2 – Acknowledgement (Sent from Aadish to Shaurya)**

| Message ID | Meaning                                  |
|------------|-------------------------------------------|
| 0x01       | Motor Forward Confirmation – Blink RB0    |
| 0x02       | Motor Reverse Confirmation – Blink RB4    |
| 0x03       | Motor Off Confirmation – Blink RB0 & RB4  |

**Function:** Updates the motor speed in Aadish’s motor driver system.

### Serial Message Format

| Field        | Example (Motor Forward) |
|--------------|--------------------------|
| Prefix       | FS                       |
| Sender ID    | S                        |
| Receiver ID  | A                        |
| Data         | 01 (Forward)             |
| Suffix       | FS                       |

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

