
## Schematic design of Motor driver Subsystem

EGR314 Aadish Lele Schematic
![Image](https://github.com/user-attachments/assets/c7163d30-6a1a-4427-86f4-89c7ff576e49)

EGR314 Motor Driver Subsystem PCB:
![Image](https://github.com/user-attachments/assets/8655c729-7e94-434b-9340-f5c528838998)

PCB Top View:  
![Image](https://github.com/user-attachments/assets/46d92fa4-020f-4745-baa7-ae3f704e8539)

PCB Bottom View:  
![Image](https://github.com/user-attachments/assets/e3679142-1249-4cea-b62b-174048852221)

Important Links:  

EGR314 Motor Driver Subsystem PDF file
[SCHEMATIC.pdf](https://github.com/user-attachments/files/19829832/SCHEMATIC.pdf)

EGR314 PCB Gerber file zip:
[PCB_gerber.zip](https://github.com/user-attachments/files/20045509/PCB_gerber.zip)

# Functional Analysis of the Schematic: Meeting User Needs and Product Specs
The schematic is a clear-cut hardware design created in Altium Designer, consisting of several neatly labeled sections. It integrates power regulation, SPI motor control, UART comms, and programming/debugging functionality to achieve the main goal: demonstrating how temperature change can dynamically control motor rotation within a modular, STEM-themed display.  

1. Neatly Sectionalized Structure for Modularity and Debugging  
The schematic is divided into headed blocks capturing functional areas:  
- Switching Voltage Regulator  
- Motor Driver  
- PIC18F47Q10 Microcontroller  
- Ribbon UART & Power Connectors  
- Snap Programmer Header  
- Test Points  
- Debug LEDs
  
The compartmentalization of the schematic makes it easy to understand, modify, and debug—key product specifications in tutorial and interactive systems. Net labels like CSN, SCK, SI, and SO also make tracing communication lines from section to section easy.  

Motor Driver Control via SPI – Real-Time Actuation  
The IFX9201SGAUMA1 motor driver talks to the PIC18F47Q10 using four SPI signals:
- CSN (Chip Select)  
- SCK (Clock)  
- SI (Serial Input)  
- SO (Serial Output)  
OUT1 and OUT2 motor outputs are connected to test points for easy probing or direct connection to motors. The outputs are driven from temperature inputs, addressing the requirement of actuating from sensor-driven information—a critical user need in control systems and embedded engineering.  

UART Data Reception – Sensor PCB Integration  
There are two ribbon connectors (CONN_IN and CONN_OUT) for UART data on the schematic:  
- CONN_IN: accepts RX data from an external temperature sensor PCB.  
- CONN_OUT: transmits TX data, maybe as status or feedback.  

The UART interface addresses the requirement for inter-device communication and sensor integration modularity, which is crucial for scalable and pedagogically significant hardware demonstrations.  

Switching Regulator-Based Power Management:    
A specialized AP62300WU-7 switching voltage regulator controls input voltage to a reliable 5V supply used throughout the circuit. This delivers:
- Power efficiency
- Smooth operation of the PIC and motor driver
- Protection from undervoltage conditions
- Smooth power delivery allows for extended use in display applications without overheating or noise interference.

Onboard Programming and Debugging:  
The schematic includes:  
- An 8-pin Snap Programmer header for programming code into the PIC18F47Q10.  
- A pull-up resistor and decoupling cap MCLR circuit for proper reset operation.  
- Test points on key SPI and ICSP lines.  
- Debugging LEDs (LED-PIC and LED-Power Debug) tied to GPIOs for providing instant visual feedback of device status.  

All the above cater to the user's need for ease of development, testability, and debuggability, which are critical in academic and prototyping environments.

Educational Demonstrability and Interactivity  
By allowing users to:
- Watch LED indicators,
- Connect motors directly via test points, debugging is simplified, and activities can be directly understood.
- Send and receive UART messages,
- And display behavior as a reaction to temperature, the schematic satisfies product requirements for a STEM-themed, interactive physical system that clearly and effectively demonstrates embedded concepts.  

Conclusion  
The functionality of this schematic is carefully crafted to meet technical as well as educational purposes. It demonstrates good system modularity, effective real-time control, standard communication protocols and clear visual feedback mechanisms. All of which are directly in accordance with the needs of students, teachers, and users viewing the project as part of an internet-enabled, interactive STEM exhibition. The design is sound and pedagogically effective, evidencing good engineering practice and thoughtful system integration.  

# Team Design and Decision making process  
Our team designed this final design of the PCB after many iterations of switching component libraries, updating footprints and ordering them in 2 batches. The PCB is designed on 100 mm X 100 mm board size and is a 2 layer PCB with VIAs. In this schematic and pcb we decied to use the same voltage regulator for easier functionality to integrate both of the PCBs to get the sensor actuator system functioning correctly.  

# Version 2.0 Improvements  
Proposed Improvements for Version 2 of the Schematic and PCB  
If I were to create a Version 2 of the schematic and PCB, I would focus on improving both the functionality and efficiency of the design, with an emphasis on readability, manufacturability, and professional presentation. The following enhancements would be implemented:  

Improved Use of Netlabels for Clarity  
While the current design does include some netlabels, Version 2 would fully standardize their use across all signal and power lines. This would:  
  - Reduce visual clutter from long, overlapping wires.  
  - Make the schematic cleaner and easier to read.  
  - Improve traceability between different schematic blocks.  
  - Using consistent and descriptive netlabel naming conventions (e.g., UART_TX, SPI_CLK, PWM_OUT) would further simplify debugging and documentation.  

Simplified and More Intuitive Wiring  
To enhance circuit readability, I would reorganize component placement to minimize crossovers and tightly group related components. This would:  
  - Help new users or reviewers quickly understand signal flow.  
  - Reduce confusion when editing or expanding the schematic later.  
  - Allow easier schematic-to-PCB correlation during layout.  

Smaller PCB Footprint for Cost Efficiency  
For Version 2 of the PCB, I would optimize the board layout to reduce the physical size of the PCB without compromising performance. This includes:  
  - Compact placement of passive components.  
  - More efficient routing using internal layers if needed.  
  - Reconsidering connector and test point placement to save space.  
A smaller board results in:  
  - Lower fabrication costs (especially in volume).  
  - Shorter manufacturing time.  
  - Potentially better mechanical integration into enclosures or displays.  

Improved Silkscreen and Labeling
Clear component labels and functional annotations on the silkscreen layer would be added to:  
  - Help identify test points, headers, and polarity.  
  - Assist with manual assembly or inspection.  
  - Improve the user experience in educational or demonstration settings.  

Potential Expansion Headers:
To future-proof the design, I may include additional headers or expansion points in Version 2 for:  
  - Extra UART/SPI/I2C peripherals.  
  - Future sensor inputs.  
  - Power monitoring or wireless modules.  

Summary
In summary, Version 2 of the schematic and PCB would emphasize:  
- Better organization through full netlabel use.  
- Cleaner schematic layout with simplified wiring.  
- Smaller, cost-efficient PCB size.  
- Enhanced usability with clear labeling and expansion options.  
These improvements would lead to a more professional, maintainable, and scalable design while continuing to support the project's STEM and educational goals.
