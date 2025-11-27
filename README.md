# **Smart Humidity & Mold Prevention System**

## **Project Overview**

This project is a Proof-of-Concept (PoC) simulation for a **Smart Humidity & Mold Prevention System**. It builds upon our initial proposal for IoT-enabled intelligent buildings by focusing on a specific, high-impact application: preventing mold growth by intelligently controlling indoor humidity. This is particularly relevant for environments like Varanasi with high seasonal humidity.

The system uses a network of simulated IoT sensors to monitor environmental conditions, a central processing unit to analyze the data and predict mold risk, and a live dashboard for remote monitoring and control.

## **System Architecture**

The simulation demonstrates the end-to-end data flow of the proposed system using the **MQTT protocol**, a standard for IoT communication.

1. **sensor\_node.py (Sensing Layer)**: Simulates multiple IoT nodes placed in different rooms (e.g., Bathroom, Basement). These nodes generate realistic temperature and humidity readings and **publish** them to unique MQTT topics.  
2. **prevention\_system.py (Processing & Analytics Layer)**: This is the core "brain" of the system. It **subscribes** to all sensor topics and performs two key tasks:  
   * **Real-time Monitoring:** It logs incoming data.  
   * **Predictive Analytics:** It calculates a **Mold Risk Score** based on a simplified model where sustained high humidity (\> 70%) and moderate temperatures (\> 20°C) increase the risk over time. When the risk score crosses a threshold, it prints a control action (e.g., "ACTIVATE DEHUMIDIFIER").  
3. **dashboard\_app.py & index.html (Visualization & Control Layer)**: A web application built with Flask and Socket.IO. The backend subscribes to MQTT data and pushes it in real-time to the index.html frontend, which displays the live status and mold risk for each room.

## **How to Run the Simulation**

### **1\. Prerequisites**

* Python 3.x  
* pip

### **2\. Installation**

Navigate to the project directory in your terminal and install the required Python packages:

\# Navigate to the project directory  
cd Mold\_Prevention\_Project

\# Install dependencies  
pip install \-r requirements.txt

### **3\. Running the Components**

You need to run the components in **three separate terminal windows**.

**Terminal 1: Start the Sensor Simulator**

python src/sensor\_node.py

**Terminal 2: Start the Prevention System Logic**

python src/prevention\_system.py

**Terminal 3: Start the Web Dashboard**

python src/dashboard\_app.py

Now, open a web browser and navigate to **http://127.0.0.1:5000** to see the live dashboard.


