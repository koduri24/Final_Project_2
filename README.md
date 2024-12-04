<h1 style="text-align: center;">Design The Circuit-level Implementation Of A Configurable Logic Block (CLB) Comprised Of A Single Basic Logic Element(BLE) Including SRAM, LUT and D Flip-Flop</h1>
<p style="text-align: center; font-size: 14px; font-style: italic;">Univerisity of Pennsylvania<br>ESE5700<br></p>
<p style="text-align: center; font-size: 14px; font-style: italic;">Jiajun Chen & Venkateswara Koduri<br>12/4/2024</p>

# 1. Design Schematics
## 1.1 5T SRAM



# 2. Design Description
## 2.1 5T SRAM
### 2.1.1 Design of a 5T SRAM Cell
In this section, we propose the design of a 5T SRAM cell, as it is expected to demonstrate improved performance compared to the traditional 6T SRAM design. The key components of the 5T SRAM cell and their functions are detailed as follows:

**Key Components**
1. **Cross-Coupled Inverters:**
The 5T SRAM cell incorporates two cross-coupled inverters that serve as bistable elements for data storage. These inverters are connected such that the output of one inverter is fed into the input of the other, forming a feedback loop. This configuration ensures a stable storage of binary states (0 or 1), as it maintains either a strong 0 or a strong 1 under normal operating conditions.
2. **Inverter for Load Signal Control:**
An additional inverter is included to manage the load input signal. This inverter performs two crucial functions:

* **Transmission Gate Activation:** When the load input is high, the inverter output becomes low, enabling the PMOS gate of the transmission gate to open. This allows data to be written into the cross-coupled inverters. Conversely, when the load input is low, the transmission gate is closed, preventing any unintended write operations, thereby satisfying the load requirement (i.e., the load signal is high during SRAM write operations).
* **Precharge Disabling:** When the load input is high (during a write operation), the inverter ensures that the NMOS connected to the precharge input is turned off. This prevents the precharge circuit from discharging to 0 V during the write operation, ensuring a clear distinction between read and write states.

3. **Transmission Gate**
The design includes a transmission gate composed of one NMOS and one PMOS transistor. This gate operates as follows:

* When the load input is high, the transmission gate opens, allowing the data input to be written into the cross-coupled inverters.

* When the load input is low, the transmission gate closes, effectively isolating the data input from the storage elements.
4. **Single NMOS Transistors**
The 5T SRAM schematic features three single NMOS transistors with the following roles:

* **Word Line NMOS:** This transistor is connected to the word line. When the word line is high, it allows the stored data to be read out via the bit line output.

* **Precharge NMOS:** This transistor is connected to the precharge input. When the precharge signal is high, it charges the relevant node to 0 V to facilitate subsequent read operations.

* **Precharge-Control NMOS:** Positioned below the precharge NMOS, this transistor ensures that the precharge mechanism is disabled during write operations, as previously described.

### 2.1.2 Operational Description

**Writing Data**

1. **Initialization:** Before the load input is high, the word line input is kept low. Once the load input becomes high, the word line is activated (high). After the data is stored in the cross-coupled inverters, the word line input is deactivated (low) again.

2. **Data Writing:** With the load input high, the transmission gate opens, enabling the data input to pass through the NMOS connected to the word line and into the cross-coupled inverters.

3. **Binary Storage:** 
- When a 1 is written, the left inverter's NMOS and the right inverter's PMOS are activated, storing a stable 1.
- When a 0 is written, the left inverter's PMOS and the right inverter's NMOS are activated, storing a stable 0.

**Reading Data**

1. **Precharge Preparation:** Before initiating a read operation, the precharge signal is set high to prepare the circuit for the subsequent data readout.

2. **Read Activation:** The precharge signal is then deactivated (low), and the word line is activated (high). This configuration allows the stored data in the cross-coupled inverters to propagate through the NMOS connected to the word line.

3. **Data Output:** Finally, the stored data can be read from the bit line output.












# 3. Design Validation/Verification
## 3.1 SRAM

# 4. Design Metric Test Cases

# 5. Design Metrics

## 5.1 Frequency

## 5.2 Average Energy

## 5.3 Area

## 5.4 Free DRC/LVS Points

## 5.5 FOM

# 6. Reasonable Quality of Results

# 7. Design Process Writeup
