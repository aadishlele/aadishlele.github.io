## Individual Block Diagram

EGR314 Individual Block Diagram   
![Image](https://github.com/user-attachments/assets/a6123ad8-b459-47c6-8e5f-b8c3a3b2238d)

EGR314 Individual Block Diagram PDF:
[BLOCKDIAGRAM.pdf](https://github.com/user-attachments/files/19830142/BLOCKDIAGRAM.pdf)

# Selection process and explaination  
The Motor Driver PCB block diagram is organized into three primary sections: Connections, Motor Driver, and the PIC18F47Q10 Microcontroller.  

**Motor Driver Section**:  
This component features two output pins that connect directly to the motor, enabling directional control. It also includes two SPI communication pins that  interface with the PIC microcontroller for receiving control commands.  

**PIC18F47Q10 Microcontroller Section**:
The PIC18F47Q10 is responsible for controlling the motor via SPI communication. It connects to the motor driver through four SPI pins:  
- CSN (Chip Select)  
- SCK (Serial Clock)  
- SI (Serial Input)  
- SO (Serial Output)   
Additionally, the PIC has two UART pins:    
-  RX (Receiver) connected to the Connector IN via ribbon cable   
-  TX (Transmitter) connected to the Connector OUT via ribbon cable   

**Connections Section**:  
This section contains the ribbon cable interfaces for UART communication. The RX pin receives incoming data via the Connector IN, and the TX pin sends outgoing data via the Connector OUT.  
The block diagram was designed by first identifying and separating the core components, then listing all relevant pins for each. Once the interconnections between components were finalized, the diagram was completed to reflect the full communication and control pathways.  
