# 🍓 Raspberry Pi Setup Guide for Linux

<div align="center">

![Raspberry Pi](https://img.shields.io/badge/Raspberry%20Pi-A22846?style=for-the-badge&logo=Raspberry%20Pi&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![C](https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)

A complete step-by-step guide for configuring a Raspberry Pi on a Linux system — from OS installation to I2C sensor communication.

</div>

---

## 📋 Table of Contents

- [Prerequisites](#-prerequisites)
- [1. Install Raspberry Pi Imager](#1-install-raspberry-pi-imager)
- [2. Flash the OS](#2-flash-the-os)
- [3. First Boot & Login](#3-first-boot--login)
- [4. Install Compilers](#4-install-compilers)
  - [GCC (C)](#gcc-c-compiler)
  - [G++ (C++)](#g-c-compiler)
  - [Python 3](#python-3)
- [5. I2C Sensor Communication](#5-i2c-sensor-communication)
- [6. Recommended Next Steps](#6-recommended-next-steps)

---

## ✅ Prerequisites

Before you begin, make sure you have:

- A Linux machine (Ubuntu/Debian recommended)
- A Raspberry Pi board (any model)
- A microSD card with **35 GB or more** storage
- A microSD card reader
- A Micro HDMI → HDMI cable
- A USB keyboard
- An external monitor

---

## 1. Install Raspberry Pi Imager

Download the latest `.deb` package:

```bash
wget https://downloads.raspberrypi.org/imager/imager_latest_amd64.deb
```

Install it:

```bash
sudo apt install ./imager_latest_amd64.deb
```

> 💡 If you encounter dependency errors, run:
> ```bash
> sudo apt --fix-broken install
> ```

Launch the Imager:

```bash
rpi-imager
```

---

## 2. Flash the OS

### Step-by-step in the Imager UI

1. **Choose Device** — Select your Raspberry Pi model
2. **Choose OS** — Select `Raspberry Pi OS Lite (64-bit)` *(recommended for this guide)*
3. **Advanced Settings** — Before flashing, press:

   ```
   Ctrl + Shift + X
   ```

   Configure the following in the advanced settings menu:

   | Setting | Recommended Action |
   |---|---|
   | SSH | Enable with password authentication |
   | Wi-Fi | Configure your external Wi-Fi credentials |
   | Locale | Set your local time and country |
   | Hostname | Assign a custom hostname |

   > 📝 **Tip:** Save all credentials and configuration details in a text editor or secure password manager before proceeding.

4. **Choose Storage** — Select your microSD card
5. **Flash** — Click *Write* and wait for the process to complete

### ⚠️ Important Notes

- Flashing **erases all existing data** on the memory card
- Take a backup of any important data before proceeding
- Use a **new or freshly formatted** memory card for best results

---

## 3. First Boot & Login

1. Safely eject the microSD card from your Linux machine
2. Insert it into the **slot on the underside** of the Raspberry Pi board
3. Connect the Raspberry Pi to a monitor using a **Micro HDMI → HDMI cable**

   > ⚠️ Connect to a **monitor only**. Connecting to a CPU/desktop display unit may cause the OS output to not render correctly.

4. Power on the board and wait for the boot process to complete
5. Log in using the credentials you saved during the Imager setup

Since **Raspberry Pi OS Lite** has no GUI, you will land directly in the terminal. Connect a USB keyboard to interact with the board.

---

## 4. Install Compilers

Before installing anything, update your package lists:

```bash
sudo apt update && sudo apt upgrade -y
```

---

### GCC (C Compiler)

Install GCC:

```bash
sudo apt install gcc -y
```

Verify the installation:

```bash
gcc --version
```

**Test it with a Hello World program:**

```bash
nano test.c
```

Paste the following:

```c
#include <stdio.h>

int main() {
    printf("C is working!\n");
    return 0;
}
```

Save and exit Nano:

| Action | Shortcut |
|---|---|
| Save file | `Ctrl + O`, then `Enter` |
| Exit Nano | `Ctrl + X` |

Compile and run:

```bash
gcc test.c -o test
./test
```

**Expected Output:**
```
C is working!
```

---

### G++ (C++ Compiler)

Install G++:

```bash
sudo apt install g++ -y
```

Verify the installation:

```bash
g++ --version
```

> You can test C++ using the same workflow as the C compiler above.

---

### Python 3

Install Python 3 and pip:

```bash
sudo apt install python3 python3-pip -y
```

Verify the installation:

```bash
python3 --version
```

**Quick test in the Python REPL:**

```bash
python3
```

```python
>>> print("Python is working!")
Python is working!
>>> exit()
```

---

## 5. I2C Sensor Communication

This section is essential for electronics and robotics projects involving I2C devices such as:

- 🔵 BNO055 (IMU Sensor)
- 🔵 MPU6050 (Gyroscope/Accelerometer)
- 🖥️ OLED Displays
- 🕐 RTC Modules
- 🔌 Any other I2C peripheral

### Install I2C Tools

```bash
sudo apt update
sudo apt install -y i2c-tools python3-smbus
```

### Verify I2C is Enabled

```bash
ls /dev/i2c-*
```

**Expected Output:**
```
/dev/i2c-1
```

This confirms that the I2C interface is active and ready for sensor communication.

---

## 6. Recommended Next Steps

Now that your Raspberry Pi is fully set up, here are some things you can explore:

- 🔐 **SSH Communication** — Access your Pi remotely from another machine
- 🌐 **Ethernet Communication** — Set up a wired network connection
- 🔌 **Sensor Interfacing** — Connect and read data from I2C/SPI sensors
- 📊 **CSV Data Logging** — Log sensor data to files using Python
- 🤖 **Python Automation** — Automate tasks and hardware interactions
- 🚤 **Robotics & ROV Development** — Build autonomous systems

---

## 📁 Repository Structure

```
raspberry-pi-setup/
├── README.md          # This guide
├── test.c             # Sample C program
└── sensors/           # Sensor interfacing scripts (coming soon)
```

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!  
Feel free to open an issue or submit a pull request.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

<div align="center">
  Developed for Raspberry Pi-based electronics and robotics projects 🤖
</div>
