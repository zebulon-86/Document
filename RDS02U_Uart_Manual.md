# Introduction

RDS02U is a lightweight millimeter-wave radar sensor. This product actively transmits a 77GHz electromagnetic wave to the front direction and processes the echo signal to determine whether there is an obstacle in front and feedback the obstacle range, speed, azimuth and other information from the radar guide radar carriers such as drones to avoid obstacles autonomously to ensure their safe operation.

# Highlights:

1. The transmitter and receiver antennas use 2 transmitter and 4 receiver MIMO arrays, the azimuth field range is 34 degrees, and the Angle resolution and Angle measurement accuracy are high.
2.  The operating frequency is 77GHz\~81GHz, which has the advantages of moving target sensitivity and high range measurement accuracy.
3.  Effective detection range is 27m;
4.  Supports output over the UART protocol, with a default baud rate of 115200.
5.  The signal processing and control unit uses a monolithic DSP +ARM dual-core architecture to run algorithms such as radar data processing, target detection and target tracking on an internal high-speed digital signal processor.

# Performance Parameters

Table 1 Performance Parameters

| **Item**                  | **Parameter Name**         | **Performance** **Specification** |
|---------------------------|----------------------------|-----------------------------------|
|   **Antenna performance** | Horizontal beam width      | ±17°                              |
|                           | Vertical beam width        | ±3°                               |
|                           | EIRP(dBm)                  | 30                                |
|   **Radar performance**   | Range Scope(m)             | 1.5\~27                           |
|                           | Range Accuracy(m)          | \<0.1                             |
|                           | Range Resolution(m)        | 0.12                              |
|                           | Frequency Band(GHz)        | 77 - 81                           |
| **Radar properties**      | Frame Rate(Hz)             | 20                                |
|                           | Modulation Bandwidth (GHz) | 1.5                               |
|                           | Working Voltage(V)         | 8 - 24                            |
|    **System properties**  | Temperature(°C)            | -40 - 85                          |
|                           | Power(W)                   | 2                                 |
|                           | Waterproof Level           | IP67                              |
|                           | Interface                  | UART                              |
|                           | Dimension(mm)              | 50\*50\*7.8                       |

# Product Physical Drawing

![](media/9817769bdfe078c4ed509e4608464c9b.jpeg)

Figure 1 RDS02U Physical Image

# Installation Method

RDS02U radar installation steps:

-   Installation location: Radar horizontal beam ±17°, vertical beam ±3° beam range shall not have any occlusion.
-   Installation direction: The radar transceiver antenna is located at the arrow on the back of the radar. During installation, the arrow on the back of the radar is up and the radar is facing the UAV.
-   Installation Angle: When the radar is installed, the antenna surface (the front of the radar) points directly in front of the UAV. According to the maximum downward inclination Angle of the UAV's flying attitude, the radar is installed by tilting upward. The optimal installation Angle is the same as the aircraft flying.

# Quick Use Steps

### Pin Definition

Interface pin definitions for RDS02U sensors, as shown in Table 2:

Table 2 RDS02U Pin Interface Definition

| **Pin** | **Wiring harness identification** | **Wiring harness color** | **Definition**|
|---------|-----------------------------------|--------------------------|-----|
| 1       | VCC                               | red                      | positive pole|
| 2       | GND                               | black                    |  negative pole|
| 3       | TX_CAN_H                          | green                    | TX|
| 4       | RX_CAN_L                          | white                    | RX|

### Data Analysis

![](media/2cb99f12d1e66e6221800d582b3a7891.jpeg)The RDS02U sensor directly outputs the Y coordinate of the nearest obstacle, as shown in the figure below. Obstacle 1 is not within the range of the radar beam and cannot be detected by the radar. In obstacle 2, 3 and 4, obstacle 2 is closest to the radar Y2, and the final output value of the radar is Y2.

Figure 3 Blind Zone and Object Detected

The serial port has a baud rate of 115200, supports only 3.3V level, data refresh rate of 20Hz, and data unit (cm). The serial port sends data packets in the specified format as required by the customer, and each packet is executed according to the customer's protocol.

RDS02U message definitions are shown in the table below:

Table 3 RDS02U Radar Frame Message Definition

| Define       | Code  | Bytes |
|--------------|-------|-------|
| Frame Head   | 5555H | 2     |
| Address code | ADD   | 1     |
| Error code    | ERR   | 1 |
| Function code | FC    | 2 |
| Length        | L     | 2 |
| Data          | DATA  | N |
| Check code    | CRC   | 1 |
| End of Frame  | AAAAH | 2 |

Frame is the basic unit for transmitting data, as shown in Table 2. The sequence of data transmission is small endian. The low byte is transmitted first, and then the high byte is transmitted.

# Precautions For Product Use

- During the transportation, storage, working and taking of the radar, it is necessary to fully protect the static electricity. For example, when there is no target object within the radar detection coverage, the radar continuously outputs irregular targets or when the DC voltage values such as power supply voltage and source current When it is in the normal range, the output signal cannot be obtained, and the radar may be damaged.
- Please keep the radar cover clean when installing. To clean the cover, need to wipe it with a soft damp cloth, and then dry it naturally;
- Please pay attention to the shape of the radar during installation, ensure that the installed radar is not deformed, and do not squeeze, bump, or hit; when installing, ensure that the radar is a factory part,

and do not self-disassemble and self-install.

# Frequently Asked Questions (FAQ)

1.  What is the radar detection range?Why is the minimum detection distance 1.5m?
    Obstacle avoidance detection range of UAV is 1.5-27m. Considering the length of the wing, it needs to stop when the UAV is 1.5m away from the obstacle, so the minimum detection distance is 1.5m.

2.  The best installation Angle does not count. Is there any reference Angle for installation?
    According to the above installation Angle Suggestions and our testing results, general flight control tilt 12° installation is recommended.

3.  Is there any data output when the radar does not detect the obstacle?
	The radar outputs data in real time. When the radar does not detect an obstacle or the distance of the obstacle is greater than 30m, the output data is 0; when the radar detects an obstacle, the output is the actual distance of the obstacle.

If encounter in the installation process cannot solve the problem, please contact the customer service of Benewake (Beijing) Co., Ltd.
