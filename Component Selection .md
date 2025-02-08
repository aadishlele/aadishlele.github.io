EGR314: Aadish Lele Team 309

Professor Nichols

Subsystem: Motor Driver

1.  Motor Driver

<table>
<colgroup>
<col style="width: 4%" />
<col style="width: 34%" />
<col style="width: 29%" />
<col style="width: 31%" />
</colgroup>
<thead>
<tr class="header">
<th>No.</th>
<th>Solution</th>
<th>Pros</th>
<th>Cons</th>
</tr>
<tr class="odd">
<th>1</th>
<th><p><img src=[![Motor_Driver_Option1](https://github.com/user-attachments/assets/bd9a74ba-cc2c-4593-80a3-87e60c3e81da)]
style="width:1.81181in;height:1.82078in" /></p>
<p>Option 1: <mark>IC MTR DRV BIPLR 2.75-6.8V 10 SOP</mark></p>
<p><mark>Texas Instrument</mark></p>
<p><mark>Price: $2.09/unit</mark></p>
<p><a
href="https://www.digikey.com/en/products/detail/texas-instruments/DRV8830DGQR/2520903"><mark><u>Option
Link</u></mark></a></p>
<p><a
href="https://www.ti.com/general/docs/suppproductinfo.tsp?distId=10&amp;gotoUrl=https%3A%2F%2Fwww.ti.com%2Flit%2Fgpn%2Fdrv8830"><mark><u>Datasheet
Link</u></mark></a></p></th>
<th><ul>
<li><p>Contains precise speed and direction control using a PIC with
minimum use of GPIO pins.</p></li>
<li><p>Operates at low voltages (2.75V–6.8V) with a small
package.</p></li>
</ul></th>
<th><ul>
<li><p>The I²C interface may get slight control delays which is bad for
our project.</p></li>
<li><p>Can only supply 1A peak, which is insufficient for motors with
larger torque</p></li>
</ul></th>
</tr>

<tr class="header">
<th>2</th>
<th><p><img src="media/image1.png"
style="width:1.93448in;height:1.94406in" /></p>
<p>Option 2: <mark>48-V, 3.5-A H BRIDGE MOTOR DRIVE</mark></p>
<p><mark>Texas Instruments</mark></p>
<p><mark>Price: $1.79/unit</mark></p>
<p><a
href="https://www.digikey.com/en/products/detail/texas-instruments/DRV8251ADDAR/16182453"><mark><u>Option
2 Link</u></mark></a></p></th>
<th><ul>
<li><p>Wide Voltage Range (3.3V–48V) - supports many motors.</p></li>
<li><p>Provides up to 4A-5A peak current for controlling larger
motors.</p></li>
<li></li>
</ul></th>
<th><ul>
<li><blockquote>
<p>Only controls one motor, so additional drivers are needed for
multi-motor applications.</p>
</blockquote></li>
<li><blockquote>
<p>Does not have a PWM module, meaning an external PWM control is
required.</p>
</blockquote></li>
<li><blockquote>
<p>Cannot be used for stepper motors or other complex motor types.</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>3</th>
<th><p><img src="media/image3.png"
style="width:1.82813in;height:1.82813in" /></p>
<p>Option 3: <mark>IC MOTOR DRIVER UNIPOLAR 8SO POWERPAD</mark></p>
<p><mark>Texas Instruments</mark></p>
<p><mark>Price: $2.13/unit</mark></p>
<p><a
href="https://www.digikey.com/en/products/detail/texas-instruments/DRV8872DDAR/5428829"><mark><u>Option
3 Link</u></mark></a></p></th>
<th><ul>
<li><p>High Current Output (Up to 3.6A Peak) – Able to drive
medium-power DC motors.</p></li>
<li><p>Wide Voltage Range (6.5V–45V) – Supports a broad range of DC
motors.</p></li>
</ul></th>
<th><ul>
<li><blockquote>
<p>At high currents, may require a heatsink or proper PCB design to
avoid shorting or fire.</p>
</blockquote></li>
<li><blockquote>
<p>Not compatible with I2C or SPI interface which is the communication
protocol for this project.</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

**Final Choice**: Option 1

**Rationale**: The Texas Instruments DRV8830DGQR is my choice for
controlling the Adafruit motor in the spinning motor top project because
of its precise speed control, low power consumption, and compact design.
It also inculcates I2C protocol and low voltage as power.Moreover, it
has a compact design and is very lightweight.

2.  Motor

<table>
<colgroup>
<col style="width: 4%" />
<col style="width: 34%" />
<col style="width: 35%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>No.</th>
<th>Solution</th>
<th>Pros</th>
<th>Cons</th>
</tr>
<tr class="odd">
<th>1</th>
<th><p><img src="media/image5.png"
style="width:1.47917in;height:1.48611in" /></p>
<p>Option 1: <mark>STANDARD MOTOR 9100 RPM 6V</mark></p>
<p><mark>Adafruit Industries</mark></p>
<p><mark>Price: $1.95/unit</mark></p>
<p><a
href="https://www.digikey.com/en/products/detail/adafruit-industries-llc/711/5353610?gQT=1"><mark><u>Option
Link</u></mark></a></p>
<p><a
href="https://mm.digikey.com/Volume0/opasdata/d220001/medias/docus/1040/711_Web.pdf"><mark><u>Datasheet
Link</u></mark></a></p></th>
<th><ul>
<li><p>Provides a stable <strong>10W power supply</strong>, making it
suitable for advanced microcontrollers like PIC.</p></li>
<li><p>Small in size and can fit physically into small systems.</p></li>
<li><p>Standard <strong>5.5mm outer</strong> DC plug ensures connections
and compatibility with other electronic ports.</p></li>
</ul></th>
<th><ul>
<li><blockquote>
<p>Fixed at <strong>5V</strong>, so we may need a Voltage regulator to
get 5V.</p>
</blockquote></li>
<li><blockquote>
<p>Cannot connect to USB Voltage regulators</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>2</th>
<th><p><img src="media/image8.png"
style="width:1.86458in;height:1.86111in" /></p>
<p>Option 2: <mark>STANDARD MOTOR 12850 RPM 6V</mark></p>
<p><mark>NMB Technologies</mark></p>
<p><mark>Price: $5.22/unit</mark></p>
<p><a
href="https://www.digikey.com/en/products/detail/nmb-technologies-corporation/PAN14EE12AA1/2417070"><mark><u>Option
2 Link</u></mark></a></p></th>
<th><ul>
<li><p>Produced by NMB Technologies, known for long lifespan in
industry.</p></li>
<li><p>Ideal for electronic cooling surfaces</p></li>
</ul></th>
<th><ul>
<li><blockquote>
<p>Is not compatible for control neither by PWM or Voltage</p>
</blockquote></li>
<li><blockquote>
<p>Will require detailed soldering instead of adapted connections</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>3</th>
<th><p><img src="media/image4.png"
style="width:1.86458in;height:1.86111in" /></p>
<p>Option 3: <mark>STANDARD MOTOR 6960 RPM 12V</mark></p>
<p><mark>Seeed Technologies</mark></p>
<p><mark>Price: $5.22/unit</mark></p>
<p><a
href="https://www.digikey.com/en/products/detail/seeed-technology-co-ltd/108990009/5487802"><mark><u>Option
3 Link</u></mark></a></p></th>
<th><ul>
<li><p>Compatible with 30V - 250V ADC</p></li>
<li><p>Uses a groove connector easy to connect to Arduino</p></li>
</ul></th>
<th><ul>
<li><blockquote>
<p>Digikey discontinued its production</p>
</blockquote></li>
<li><blockquote>
<p>Has a limited lifespan over other options</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

**Final Choice**: Option 1

**Rationale**: The Adafruit motor provides consistent torque, stable
power supply of 10W, and reliable performance and it works excellent
with PIC microcontrollers. Its compact design and efficiency make it
ideal for installing it into small handheld devices like a motor based
spinning top which is the main inspiration of our project.

3.  Voltage Regulator

<table>
<colgroup>
<col style="width: 4%" />
<col style="width: 34%" />
<col style="width: 35%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>No.</th>
<th>Solution</th>
<th>Pros</th>
<th>Cons</th>
</tr>
<tr class="odd">
<th>1</th>
<th><p><img src="media/image11.png"
style="width:1.88001in;height:1.88932in" /></p>
<p>Option 1: <mark>LM2675MX-3.3/NOPB</mark></p>
<p><mark>Texas Instruments</mark></p>
<p><mark>Price: $4.36/unit</mark></p>
<p><a
href="https://www.digikey.com/en/products/detail/texas-instruments/LM2675MX-3-3-NOPB/366907"><mark><u>Option
Link</u></mark></a></p>
<p><a
href="https://www.ti.com/general/docs/suppproductinfo.tsp?distId=10&amp;gotoUrl=https%3A%2F%2Fwww.ti.com%2Flit%2Fgpn%2Flm2675"><mark><u>Datasheet</u></mark></a></p></th>
<th><ul>
<li><p>Reduces heat dissipation and power loss</p></li>
<li><p>Requires minimal additional components, simplifying circuit
design and PCB layout.</p></li>
</ul></th>
<th><ul>
<li><blockquote>
<p>Fixed 3.3V Output – Not adjustable, which limits flexibility if
different voltages are needed.</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>2</th>
<th><p><img src="media/image7.png"
style="width:1.83936in;height:1.84846in" /></p>
<p>Option 2:</p>
<p><mark>MIC5158YM-TR</mark></p>
<p><mark>Price: $5.66/unit</mark></p>
<p><a
href="https://www.digikey.com/en/products/detail/microchip-technology/MIC5158YM-TR/1030155"><mark><u>Option
2 Link</u></mark></a></p></th>
<th><ul>
<li><p>More pins offer more GPIO functionality</p></li>
<li><p>Can support wide range of voltage regulation</p></li>
</ul></th>
<th><ul>
<li><blockquote>
<p>Difficult to solder.</p>
</blockquote></li>
<li><blockquote>
<p>Expensive than other voltage regulators.</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>3</th>
<th><p><img src="media/image10.png"
style="width:1.90742in;height:1.91686in" /></p>
<p>Option 3:</p>
<p><mark>MIC5156-3.3YM</mark></p>
<p><mark>Price: $4.02/unit</mark></p>
<p><a
href="https://www.digikey.com/en/products/detail/microchip-technology/MIC5156-3-3YM/1030132"><mark><u>Option
3 Link</u></mark></a></p></th>
<th><ul>
<li><p>Supports High Current Loads for transistors and SMDS</p></li>
<li><p>Ensures efficient operation with minimal voltage loss.</p></li>
</ul></th>
<th><ul>
<li><blockquote>
<p>Difficult to Solder</p>
</blockquote></li>
<li><blockquote>
<p>Requires External Components</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

**Final Choice**: Option 1

**Rationale**: The LM2675MX-3.3/NOPB offers 90% efficiency, 6.5V--40V
input range, and 1A output. The stable 3.3V regulation with minimal heat
dissipation is consistent in the IC. It has a low component count, and
built-in thermal and overcurrent protection for reliability.

4.  Power Supply

<table>
<colgroup>
<col style="width: 4%" />
<col style="width: 34%" />
<col style="width: 35%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>No.</th>
<th>Solution</th>
<th>Pros</th>
<th>Cons</th>
</tr>
<tr class="odd">
<th>1</th>
<th><p><img src="media/image12.png"
style="width:1.77731in;height:1.68932in" /></p>
<p>Option 1: <mark>9V rechargeable 13000mAH battery</mark></p>
<p><mark>LCLEBM</mark></p>
<p><mark>Price: $11.98/2 unit</mark></p>
<p><a
href="https://www.amazon.com/PAISUE-Rechargeable-Lithium-ion-Multimeter-Microphone/dp/B0B248DSFG?asc_source=01HA27KKZ797CTK9Z7EGCDH1R5&amp;gQT=1&amp;ref_=fplfs&amp;smid=A2WEVNKRB72JGE&amp;source=ps-sl-shoppingads-lpcontext&amp;tag=snxs33-20&amp;th=1"><mark><u>Option
Link</u></mark></a></p></th>
<th><ul>
<li><p>Ideal for portable electronics and has a small factor and 1200mAh
capacity.</p></li>
<li><p>Rechargeable for longer utility</p></li>
</ul></th>
<th><ul>
<li><blockquote>
<p>May not power sufficiently for high usage devices.</p>
</blockquote></li>
<li><blockquote>
<p>Will require manual soldering</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>2</th>
<th><p><img src="media/image9.png"
style="width:1.92277in;height:1.93229in" /></p>
<p>Option 2:</p>
<p><mark>L6R06H-240</mark></p>
<p><mark>Tri-Mag LLC</mark></p>
<p><mark>Price: $5.31/unit</mark></p>
<p><a
href="https://www.digikey.com/en/products/detail/tri-mag-llc/L6R06H-240/7682618"><mark><u>Option
2 Link</u></mark></a></p></th>
<th><ul>
<li><p>Supports 90V-240V input with a excellent output voltage of
24V.</p></li>
<li><p>Has maximum current output of 240 mA</p></li>
</ul></th>
<th><ul>
<li><blockquote>
<p>Will require wall mounting</p>
</blockquote></li>
<li><blockquote>
<p>Not portable</p>
</blockquote></li>
<li><blockquote>
<p>Cannot be soldered</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>3</th>
<th><p><img src="media/image6.png"
style="width:1.83675in;height:1.84584in" /></p>
<p>Option 3: <mark>SWI3-5-N-MUB</mark></p>
<p><mark>Price: $4.92/unit</mark></p>
<p><a
href="https://www.digikey.com/en/products/detail/cui-inc/SWI3-5-N-MUB/7784529"><mark><u>Option
3 Link</u></mark></a></p></th>
<th><ul>
<li><p>Supports high operating temp of 40 deg Celcius</p></li>
<li><p>Has a high current output of 600 mA</p></li>
</ul></th>
<th><ul>
<li><blockquote>
<p>Difficult to Solder</p>
</blockquote></li>
<li><blockquote>
<p>Does not support power voltage and is not compatible.</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

**Final Choice**: Option 1

**Rationale**: The 9V 13000 mAH battery is more functional and is
portable. It can fit into the spinning top unlike other power supplies
and also its pros are more inclined towards our project requirements.

Microcontroller Selection:

Requirements:  
I2C communication protocol for sending data from the motor driver to the
ESP32 and multiple GPIO pins of the PIC DIP microcontroller.

Microcontroller Considerations:  
PIC18F27Q10

\*PIC TABLE

\*Pins Table

Role Description:  
My role in the team is to program and design a motor driver and the
motor which is the heart of our project. Our project is basically a
spinning top with a HMI that will be able to control speed and direction
of our spinning top. I will be using the PIC to ensure that when data
and power are supplied, it runs and is able to balance itself on the
ground. For this it is very essential for me to get the speed and
direction of the motor right as that will smoothen the further process
of sending that data to the ESP32 module. I am responsible for actuation
using the motor and the motor driver.

\*Screenshots of MCC using the selected PIC
