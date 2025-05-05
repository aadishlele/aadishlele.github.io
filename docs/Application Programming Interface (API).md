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

\#include \<xc.h\>  
\#include \<stdint.h\>  
\#include \<stdbool.h\>  
\#define UART\_BUFFER\_SIZE 10  
\#define MSG\_PREFIX\_1 0x0001  // Change Motor Direction  
\#define MSG\_PREFIX\_2 0x0002  // Update Motor Speed  
\#define MSG\_SUFFIX\_1 0x0020  
\#define MSG\_SUFFIX\_2 0x0021  
// UART Receive Buffer  
volatile uint8\_t uartBuffer\[UART\_BUFFER\_SIZE\];  
volatile uint8\_t bufferIndex \= 0;  
// Function Prototypes  
void UART\_Init(void);  
void UART\_Send(uint8\_t \*message, uint8\_t length);  
void Process\_Message(uint8\_t \*message, uint8\_t length);  
void UART\_Receive\_Handler(void);  
void UART\_Init(void) {  
    // Configure UART for 9600 baud, 8-N-1  
    SPBRG \= 25; // Adjust for different baud rates  
    TXSTAbits.BRGH \= 1;  
    RCSTAbits.SPEN \= 1; // Enable UART  
    RCSTAbits.CREN \= 1; // Enable Reception  
    TXSTAbits.TXEN \= 1; // Enable Transmission  
    // Enable Interrupts  
    PIE1bits.RCIE \= 1;  
    INTCONbits.PEIE \= 1;  
    INTCONbits.GIE \= 1;  
}  
void UART\_Send(uint8\_t \*message, uint8\_t length) {  
    for (uint8\_t i \= 0; i \< length; i++) {  
        TXREG \= message\[i\];  
        while (\!TXSTAbits.TRMT);  
    }  
}  
void Process\_Message(uint8\_t \*message, uint8\_t length) {  
    uint16\_t prefix \= (message\[0\] \<\< 8\) | message\[1\];  
    uint16\_t suffix \= (message\[6\] \<\< 8\) | message\[7\];  
    if (prefix \== MSG\_PREFIX\_1 && suffix \== MSG\_SUFFIX\_1) {  
        uint8\_t motor\_direction \= message\[4\];  
        // Apply motor direction change here  
    }  
    else if (prefix \== MSG\_PREFIX\_2 && suffix \== MSG\_SUFFIX\_2) {  
        uint16\_t motor\_speed \= message\[4\];  
        // Apply motor speed update here  
    }  
    uint8\_t ack\_msg\[\] \= {message\[0\], message\[1\], 0x01};  
    UART\_Send(ack\_msg, 3);  
}  
void UART\_Receive\_Handler(void) {  
    if (PIR1bits.RCIF) {  
        uint8\_t receivedByte \= RCREG;  
        if (bufferIndex \== 0 && receivedByte \!= 0x00) {  
            uartBuffer\[bufferIndex++\] \= receivedByte;  
        } else if (bufferIndex \> 0\) {  
            uartBuffer\[bufferIndex++\] \= receivedByte;  
            if (bufferIndex \>= UART\_BUFFER\_SIZE) {  
                Process\_Message(uartBuffer, bufferIndex);  
                bufferIndex \= 0;  
            }  
        }  
    }  
}  
