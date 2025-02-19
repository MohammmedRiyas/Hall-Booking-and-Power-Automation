# Hall Booking and Power Automation System

## Overview
The **Hall Booking and Power Automation System** is an innovative solution designed to optimize energy usage and automate the power supply in rooms based on user needs. The system integrates room booking, power management, and IoT automation to provide a seamless user experience.

Users can scan a **QR code** in a room to book power for a specific duration. Once booked, the system activates power via a relay connected to an **ESP32-based controller** and automatically turns it off after the set duration, improving energy efficiency and reducing unnecessary power wastage.

---
## Features
### **Room Booking via QR Code**
- Each room has a **unique QR code**.
- Users scan the QR code using a mobile app.
- The app allows users to set a **power duration**.
- The system checks room availability and grants power access for the set duration.

### **Automated Power Control**
- Uses **ESP32 with an Ethernet Shield** to communicate with a relay and buzzer.
- Controls power supply for devices like **lights, air conditioning, and electrical appliances**.
- Communicates via the **MQTT protocol over Ethernet** to ensure reliable communication between the server, mobile app, and the device.

### **Time-Based Power Management**
- Power is enabled for the booked duration and a **countdown timer** is displayed.
- **10-minute warning buzzer:** Alerts users when only 10 minutes remain before power cutoff.
- Power is **automatically disconnected** after the booked duration ends.

### **Device Communication**
- Uses **MQTT (Message Queuing Telemetry Transport)** for efficient, low-latency communication.
- Works over **Ethernet** for a stable and reliable connection, avoiding Wi-Fi issues.

### **OTA Firmware Updates**
- Supports **Over-the-Air (OTA) updates**, allowing remote firmware updates for bug fixes, security patches, and new features.

---
## Hardware Requirements
- **ESP32 with Ethernet Shield** (Core controller)
- **Relay Module** (Power control)
- **Buzzer** (Alarm for 10-minute warning and power cutoff)
- **Ethernet Communication** (Wired connection for stability)
- **Smartphone with QR Code Scanner** (For booking power)

---
## Software Components
### **Mobile App**
- Allows users to **scan QR codes** and book power.
- Communicates with the backend server via **MQTT**.
- Displays **real-time power status and countdown timer**.
- Available for **Android and iOS**.

### **Backend Server**
- Manages **room availability, bookings, and user requests**.
- Sends real-time updates to **ESP32 devices**.
- Keeps track of power duration and automatically **disconnects power when time expires**.

### **MQTT Broker**
- Acts as an intermediary between **mobile app, backend server, and ESP32 devices**.
- Ensures **reliable message delivery** with minimal network overhead.

---
## System Workflow
### **1. Scanning QR Code**
- Users scan the room's **QR code** using the mobile app.
- Select the **duration** for power usage (e.g., 30 min, 1 hour, etc.).
- The request is sent to the server via **MQTT**.

### **2. Power Booking and Confirmation**
- The **server checks power availability** and confirms the booking.
- A message is sent to the **ESP32 device** to activate the relay and turn on the power.

### **3. Time Management**
- The app displays a **countdown timer**.
- When **10 minutes remain**, the **buzzer activates** as a warning.

### **4. Power Cutoff**
- After the booking time ends, the **ESP32 automatically turns off the relay**, cutting power.
- The user receives a notification via the **mobile app**.

### **5. OTA Updates**
- If updates are available, the ESP32 firmware can be updated **remotely**.

---
## Benefits
### **Energy Efficiency**
- Prevents unnecessary power usage by ensuring power is **only available when needed**.

### **Convenience**
- Users can easily **book power using a mobile app**.
- Get **timely alerts** before power cutoff.

### **Reliability**
- Uses **Ethernet** instead of Wi-Fi for **stable, uninterrupted communication**.

### **Scalability**
- Supports **multiple rooms and devices** using the **MQTT protocol**.
- Easily adaptable for **larger buildings or campuses**.

---
## Future Enhancements
- **User Authentication**: Adding login functionality for security.
- **Dynamic Pricing**: Charging based on power usage.
- **Remote Power Control**: Allowing admins to manually enable/disable power.
- **Detailed Analytics**: Monitoring power consumption trends.

---
