# 2-layer-MCU-datalogger-with-a-512k-EEPROM
# 📟 MCU Data Logger with 512KB EEPROM

## 📌 Overview

This project is a **microcontroller-based data logging system** designed to capture, store, and retrieve data using an external **512KB EEPROM**. The system ensures **non-volatile storage**, making it suitable for applications where data must persist even after power loss.

The logger collects data from input sources (sensors or internal signals), processes it, and stores it efficiently in EEPROM using structured memory management techniques.

---

## ⚙️ System Architecture

The system consists of the following core components:

* **Microcontroller (MCU)**
  Handles data acquisition, processing, and communication with EEPROM.

* **External EEPROM (512KB)**
  Stores logged data in a non-volatile format.

* **Communication Interface**
  Used for data transfer (e.g., UART / I2C / SPI).

---

## 🔄 Working Principle

### 1. Data Acquisition

The MCU reads input signals such as:

* Analog sensor data (via ADC)
* Digital inputs
* Internal system parameters

---

### 2. Data Formatting

Before storing, the data is structured into fixed-size records:

```
[Timestamp][Sensor Data][Status][Checksum]
```

This ensures consistency and simplifies retrieval.

---

### 3. EEPROM Storage

The EEPROM acts as a **byte-addressable memory space**:

* Total Size: **512 KB (524,288 bytes)**
* Data is written sequentially using a **write pointer**

---

### 4. Memory Management

#### 📍 Memory Map Example

```
0x0000 – 0x0FFF   → Configuration Data
0x1000 – End      → Logged Data
```

---
---

### 6. Data Retrieval

Stored data can be read:

* Sequentially from EEPROM
* Transmitted via communication interface (e.g., UART)

---

## 🧠 Key Design Concepts

### ✅ Non-Volatile Storage

EEPROM retains data even after power loss.

---

### ⚠️ Write Cycle Limitation

EEPROM has limited write endurance (~1 million cycles per address).

#### Solution:

* Implement **wear leveling**
* Avoid repeated writes to the same location

---

### ⚡ Write Latency

EEPROM write operations are relatively slow.

#### Solution:

* Use **RAM buffering**
* Batch writes instead of frequent single writes

---

### 🔐 Data Integrity

Power loss during write may corrupt data.
---

## 📊 Storage Capacity

Example:

* Record Size: 16 bytes
* Total Memory: 524,288 bytes

```
Total Records ≈ 524,288 / 16 = 32,768 entries
```

---
## 🧪 Features

* Efficient EEPROM memory utilization
* Circular buffer logging system
* Data integrity via checksum
* Modular firmware design
* Scalable architecture for multiple sensors

---

## 🚧 Challenges & Solutions

| Challenge        | Solution            |
| ---------------- | ------------------- |
| EEPROM wear      | Wear leveling       |
| Slow write speed | RAM buffering       |
| Power failure    | Checksum validation |
| Memory overflow  | Circular buffer     |

---

## 🚀 Applications

* IoT Data Logging
* Environmental Monitoring
* Industrial Systems
* Black Box Recording Systems

---

## 📎 Future Improvements

* Add SD card support for larger storage
* Implement real-time clock (RTC)
* Wireless data transmission (BLE/WiFi)
* Advanced compression techniques

---

## 📜 License

This project is open-source and available under the MIT License.

---

## 👨‍💻 Author

Developed by a second year electronics student so forgive me if there is any issue
