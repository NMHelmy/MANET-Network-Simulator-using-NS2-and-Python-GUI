# MANET Network Simulator using NS2 and Python GUI
This project provides a comprehensive simulation of ***Mobile Ad Hoc Networks (MANETs)*** using ***NS2 (Network Simulator 2)*** and ***Python***. The project includes simulations for both ***Proactive Routing*** and ***Reactive Routing***, along with a Python-based GUI for visualizing the differences between the two protocols. Additionally, the project includes scripts for analyzing network performance metrics such as ***throughput, packet delivery ratio (PDR), average delay, packet loss, and overhead***.

## Table of Contents
1. [Project Overview](#project-overview)
2. [Features](#features)
3. [Installation](#installation)
4. [Usage](#usage)
5. [Routing Protocols](#routing-protocols)
6. [Performance Metrics](#performance-metrics)
7. [Performance Analysis](#performance-analysis)
8. [References](#references)

---

## Project Overview
The project consists of the following components:
1. **NS2 Simulation (Tcl Script):** Simulates a MANET environment with configurable parameters such as the number of nodes, routing protocols, and source-destination pairs. The simulation generates trace files (.tr) and network animation files (.nam) for performance analysis.<br><br>
2. **Python GUI for Proactive Routing (OLSR):** A Python script that simulates proactive routing using Tkinter for the GUI. It allows users to visualize node movement, routing table updates, and packet transmission.<br><br>
3. **Python GUI for Reactive Routing (AODV):** A Python script that simulates reactive routing using Tkinter for the GUI. It demonstrates on-demand route discovery and packet transmission.<br><br>
4. **Performance Analysis Scripts:**
    - **graph.py:** A Python script that reads performance metrics from performance.txt and generates a bar chart to visualize the results.
    - **performance.awk:** An AWK script that processes the trace files generated by NS2 to calculate performance metrics such as throughput, PDR, delay, packet loss, and overhead.
    - **performance.txt:** A text file that stores the calculated performance metrics after running the NS2 simulation.

--- 
---

## Features
**NS2 Simulation (Tcl Script)**
- Configurable Parameters: Users can specify the number of nodes, routing protocol, and source-destination pairs.
- Dynamic Node Movement: Nodes move randomly within the simulation area, and the network topology updates in real-time.
- Trace and Animation Files: The simulation generates .tr (trace) and .nam (animation) files for performance analysis and visualization.

**Python GUI for Proactive Routing (OLSR)**
- Continuous Route Updates: Nodes periodically update their routing tables to maintain up-to-date route information.
- Interactive GUI: Users can start/stop node movement, send data packets, and view routing tables.
- Dynamic Node Movement: Nodes move randomly within the simulation area, and the network topology updates in real-time.
- Routing Table Visualization: Users can view the routing tables of all nodes, showing the next hop and hop count for each destination.

**Python GUI for Reactive Routing (AODV)**
- On-Demand Route Discovery: Routes are discovered only when needed, reducing overhead in highly dynamic networks.
- Interactive GUI: Users can start/stop node movement, send data packets, and observe the route discovery process.
- Dynamic Node Movement: Nodes move randomly, and the network topology updates in real-time.
- Route Discovery Visualization: Users can observe the Route Request (RREQ) and Route Reply (RREP) process as nodes discover routes.

**Performance Analysis Scripts**
- graph.py: Generates a bar chart to visualize performance metrics such as throughput, PDR, delay, packet loss, and overhead.
- performance.awk: Processes the trace files generated by NS2 to calculate performance metrics.
- performance.txt: Stores the calculated performance metrics for further analysis.

---
---

## Installation
### Prerequisites
- Ubuntu (or any Linux-based OS)
- NS2 (Network Simulator 2) with nam_1.14_amd64
- Python 3.x
- Tkinter (for the Python GUI)
- Matplotlib (for generating performance graphs)

### Steps to install
#### 1. Clone the Repository:
```
git clone https://github.com/NMHelmy/MANET-Network-Simulator-using-NS2-and-Python-GUI.git
cd MANET-Network-Simulator-using-NS2-and-Python-GUI.git
```
#### 2. Install NS2:
If you already have ns2 ensure you have the correct version of nam (Network Animator) nam_1.14_amd64.<br>
If you do not have the correct version, you can install it using the following command:
```
sudo dpkg --install nam_1.14_amd64.deb
```
#### **Step 1: Install Dependencies**
```
sudo apt update && sudo apt upgrade -y
sudo apt install build-essential autoconf automake gcc g++ perl libx11-dev xgraph xg xorg-dev libxt-dev libxmu-dev -y
```
#### **Step 2: Download and Extract NS2**
``` 
cd ~
wget https://downloads.sourceforge.net/project/nsnam/allinone/ns-allinone-2.35/ns-allinone-2.35.tar.gz
tar -xvzf ns-allinone-2.35.tar.gz
cd ns-allinone-2.35
```
#### **Step 3: Extract the Files**
```
tar -xvzf ns-allinone-2.35.tar.gz
cd ns-allinone-2.35
```
#### **Step 4: Verify Installation**
```
ns -version
nam -version
```
Expected output:
```
Ns version 2.35
Nam version 1.14
```
#### 3. Install Python Dependencies:
Ensure Python 3.x and Tkinter are installed:
```
sudo apt-get install python3-tk
```
Install Matplotlib for generating performance graphs:
```
pip install matplotlib
```

---
---

## Run the NS2 simulation
Navigate to the directory containing the Tcl script:
```
cd ns2-simulation
```
Run the simulation using the following command:
```
ns sim.tcl <Number of Nodes> <Routing Protocol> <Source Node> <Destination Node> <Second Source Node> <Second Destination Node>
```
Example:
```
ns sim.tcl 10 AODV 1 5 2 6
```
To view the simulation animation, use the nam command (nam nameOfTheProtocol_numOfNodes.nam):
```
nam AODV_10.nam
```
![ns2_ss](https://github.com/user-attachments/assets/c751c9f9-c627-4cd4-978b-761730fe5781)

---
---

## Run the Python GUI for Proactive Routing (OLSR):
Navigate to the Python GUI directory:
```
cd python-gui-proactive
```
Run the Python script:
```
python proactive_routing.py
```
OR 
```
python3 proactive_routing.py
```
![procative_ss](https://github.com/user-attachments/assets/9f77d7bd-cf22-4e72-8c5d-fa28ac4e167b)
---
---


## Run the Python GUI for Reactive Routing (AODV):
Navigate to the Python GUI directory:
```
cd python-gui-reactive
```
Run the Python script:
```
python reactive_routing.py
```
OR 
```
python3 reactive_routing.py
```
![reactive_ss](https://github.com/user-attachments/assets/4d007159-50b7-4cb9-9919-6a92dc3bbfe9)
---
---


## Analyze Performance Metrics:
After running the NS2 simulation, the performance.awk script will generate performance.txt with the calculated metrics.
#### Run the 'performance.awk' script
To analyze the performance metrics from your NS2 simulation, run the `performance.awk` script on the trace file generated by NS2 (e.g., `AODV_10.tr`). <br>Use the following command:
```
awk -f performance.awk AODV_10.tr
```
Now the calculated metrics (e.g. throughput, PDR, delay, packet loss, and overhead) is saved into performance.txt.
#### Run the graph.py script to visualize
After generating performance.txt, you can visualize the performance metrics by running the graph.py script. <br>Use the following command:
```
python graph.py
```
OR
```
python3 graph.py
```
This script reads the metrics from performance.txt and generates a bar chart to visualize the results.
![graph_ss](https://github.com/user-attachments/assets/b8406fda-b2bd-4360-a446-aa8b794540b8)
---
---


## Usage
### NS2 Simulation (Tcl Script)
1. **Run the Simulation:** Use the ns command to run the Tcl script with the desired parameters.
2. **View the Simulation Animation:** Use the nam command to view the network animation.
3. **Analyze Performance Metrics:** The simulation generates trace files (.tr) that are processed by the performance.awk script to calculate performance metrics.

### Python GUI for Proactive Routing (OLSR)
1. **Start the Simulation:** Run the proactive_routing.py script.
2. **Start Node Movement:** Click the "Start Movement" button to begin random node movement.
3. **Select Source and Destination Nodes:** Click on a node to select it as the source, then click another node to select it as the destination.
4. **Send Data:** Click the "Send Data" button to send a packet from the source to the destination. The path taken by the packet will be displayed.
5. **View Routing Tables:** Click the "Show Routing Tables" button to view the routing tables of all nodes.
6. **Stop Node Movement:** Click the "Stop Movement" button to stop node movement.

### Python GUI for Reactive Routing (AODV)
1. **Start the Simulation:** Run the reactive_routing.py script.
2. **Start Node Movement:** Click the "Start Movement" button to begin random node movement.
3. **Select Source and Destination Nodes:** Click on a node to select it as the source, then click another node to select it as the destination.
4. **Send Data:** Click the "Send Data" button to initiate the route discovery process. The path taken by the packet will be displayed.
5. **Stop Node Movement:** Click the "Stop Movement" button to stop node movement.

### Performance Analysis
1. **Run the NS2 Simulation:** The simulation generates trace files (.tr) that are processed by the performance.awk script.
2. **Generate Performance Metrics:** The performance.awk script calculates performance metrics and saves them in performance.txt.
3. **Visualize Performance Metrics:** Run the graph.py script to generate a bar chart visualizing the performance metrics.

---
---

## Routing Protocols
### Proactive Routing (OLSR)
**Definition:** Proactive routing protocols continuously update routing tables to maintain up-to-date route information.
##### Advantages:
- Immediate route availability for data transmission.
- No route discovery delay during data transfer.
- Well-suited for low-mobility environments.

##### Disadvantages:
- High overhead due to frequent route updates.
- Not suitable for highly dynamic networks.

### Reactive Routing (AODV)
**Definition:** Reactive routing protocols discover routes only when needed, on-demand.
##### Advantages:
- Lower overhead compared to proactive protocols.
- Ideal for networks with high mobility or unpredictable topology.
- Efficient in terms of bandwidth usage.

##### Disadvantages:
- Higher latency for route discovery during data transmission.
- Route discovery process can fail if no route exists.
- May lead to longer delays in real-time applications.

---
---

## Performance Metrics
The following performance metrics are calculated and visualized:
<br>**Throughput:** The rate at which data is successfully transferred from one point to another in the network.<br>
<br>**Packet Delivery Ratio (PDR):** The ratio of successfully received packets to the total packets sent.<br>
<br>**Average Delay:** The average time it takes for a packet to travel from the sender to the receiver.<br>
<br>**Packet Loss:** The percentage of packets that are sent but never reach the destination.<br>
<br>**Overhead:** The extra resources consumed by the routing protocol beyond the actual data transmission.

---
---

## Performance Analysis
The performance.awk script processes the trace files generated by the NS2 simulation to calculate the following metrics:
<br>**Throughput (kbps):** The rate of successful data transfer.<br>
<br>**PDR (%):** The percentage of packets successfully delivered.<br>
<br>**Average Delay (s):** The average time taken for packets to reach the destination.<br>
<br>**Packet Loss (%):** The percentage of packets lost during transmission.<br>
<br>**Overhead (%):** The additional resources consumed by the routing protocol.<br>
<br>The graph.py script reads the calculated metrics from performance.txt and generates a bar chart to visualize the results.

--- 
---

## References
1. [NS2 Official Documentation](http://www.isi.edu/nsnam/ns/)
2. [Python Tkinter Documentation](https://docs.python.org/3/library/tkinter.html)
3. [Matplotlib Documentation](https://matplotlib.org/stable/contents.html)
4. [GitHub Repository for SDN-MANET Reactive Firewall Simulators](https://github.com/Dimitrios-Kafetzis/SDN-MANET-reactive-firewall-simulators)
5. [GitHub Repository for NS2 MANET Simulations](https://github.com/Naheel-Azawy/ns2-manet-cmp)
