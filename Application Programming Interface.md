Each user has been assigned a user ID to make communication easier between users. Any messages sent will contain the sender and reciever ID to identify where its coming from and where its going to. Below is a list of IDs for each user in our project.  

| ID | User |
|---|---|
| 0xFF | Bruce |
| 0xFE | Baron |
| 0xFD | Aadish |
| 0xFC | Shaurya |    
  
The following in a message structure for receiving date and sednign date for me sybsystem as seen in my Team website  

| Message Type | Byte 1-2 (Prefix)<br>(uint16_t) | Byte 3 (Sender ID)<br>(uint8_t) | Byte 4 (Reciever ID)<br>(uint8_t) | Byte 5-6 (Data)<br>(uint16_t) | Byte 7-8 (Suffix)<br>(uint16_t) |
|---|---|---|---|---|---|
| 1 | 0x0001 | Bruce | Aadish | Motor Direction X | 0x0020 |
| 2 | 0x0002 | Shaurya | Aadish | Motor Speed X | 0x0021 |   

The following are the message types I will be receiving for me to update the changes on the motor.  
| Message Type | Description |
|---|---|
| 1 | Change Motor Direction |
| 2 | Update Motor Speed |   

| Message Type | Byte 1-2 (Prefix)<br>(uint16_t) | Byte 3 (Sender ID)<br>(uint8_t) | Byte 4 (Reciever ID)<br>(uint8_t) | Byte 5-6 (Data)<br>(uint16_t) | Byte 7-8 (Suffix)<br>(uint16_t) |
|---|---|---|---|---|---|
| 1 | 0x0001 | Bruce | Aadish | Motor Direction X | 0x0020 |
| 2 | 0x0002 | Shaurya | Aadish | Motor Speed X | 0x0021 |


