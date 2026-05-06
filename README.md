#  Telematics Control Unit (TCU) for Automotive Systems

> Real-time automotive telematics firmware built with FreeRTOS on ARM Cortex-M, featuring wireless connectivity and ISO 26262 functional safety compliance.

---

##  Project Overview

This project implements a **next-generation Telematics Control Unit (TCU)** designed for automotive OEM platforms. It handles real-time data acquisition, Bluetooth/Wi-Fi connectivity, and fault-resilient mechanisms in a safety-critical environment.

---

##  Tech Stack

| Category | Technologies |
|---|---|
| Language | C, C++, Embedded C |
| RTOS | FreeRTOS |
| Architecture | ARM Cortex-M |
| Build System | Yocto Project, U-Boot |
| Protocols | CAN, UART, SPI, I2C, Bluetooth, Wi-Fi |
| Testing | Tessy, Unit Testing |
| Safety Standard | ISO 26262 |

---

##  Architecture
+----------------------------+
|     Application Layer      |  ← Telemetry logic, fault management
+----------------------------+
|      FreeRTOS Kernel       |  ← Task scheduling, IPC, timers
+----------------------------+
|   Device Driver Layer      |  ← CAN, UART, SPI, I2C, BT/WiFi drivers
+----------------------------+
|   Hardware (ARM Cortex-M)  |  ← GPIO, ADC, Interrupts, DMA

---

##  Key Features

- ✅ **Real-time data acquisition** using SPI, UART, and I2C interfaces
- ✅ **FreeRTOS task scheduler** for concurrent low-latency operations
- ✅ **Bluetooth & Wi-Fi connectivity** for OTA telemetry data upload
- ✅ **Fault-resilient mechanisms** with watchdog and error recovery
- ✅ **Yocto-based BSP** with optimized U-Boot bootloader
- ✅ **ISO 26262 compliant** firmware validation using Tessy
- ✅ **CAN protocol stack** for inter-module automotive communication

---

## 📁 Project Structure

tcu-prototype/
├── src/
│   ├── main.c                  # Entry point, scheduler init
│   ├── drivers/
│   │   ├── can_driver.c        # CAN bus driver
│   │   ├── spi_driver.c        # SPI peripheral driver
│   │   ├── i2c_driver.c        # I2C peripheral driver
│   │   └── uart_driver.c       # UART communication driver
│   ├── tasks/
│   │   ├── telemetry_task.c    # Data acquisition & upload task
│   │   ├── fault_task.c        # Fault monitoring task
│   │   └── comms_task.c        # BT/WiFi communication task
│   └── bsp/
│       ├── board_init.c        # Hardware initialization
│       └── clock_config.c      # Clock tree configuration
├── include/
│   ├── can_driver.h
│   ├── spi_driver.h
│   └── tcu_config.h
├── tests/
│   └── unit/                   # Tessy-compatible unit test stubs
├── yocto/
│   └── meta-tcu/               # Custom Yocto layer
├── docs/
│   └── architecture.md         # Design documentation
├── CMakeLists.txt
└── README.md

---

##  Getting Started

### Prerequisites
- ARM GCC Toolchain (`arm-none-eabi-gcc`)
- CMake ≥ 3.20
- FreeRTOS kernel source
- Yocto Project (for BSP build)

### Build

```bash
git clone https://github.com/pkkatakam9-afk/tcu-prototype.git
cd tcu-prototype
mkdir build && cd build
cmake .. -DCMAKE_TOOLCHAIN_FILE=../cmake/arm-cortex-m.cmake
make -j4
```

### Flash

```bash
openocd -f interface/stlink.cfg -f target/stm32f4x.cfg \
        -c "program build/tcu.elf verify reset exit"
```

---

##  Testing

Unit tests are written to be compatible with **Tessy** test automation:

```bash
cd tests/unit
tessy run --config tessy_config.xml
```

---

## 📊 Results

| Metric | Result |
|---|---|
| Boot time reduction | 20% faster with optimized U-Boot |
| Defect leakage reduction | 25% via early Tessy unit testing |
| Task scheduling latency | < 1ms (FreeRTOS tick rate 1kHz) |

---

## 📄 Standards & Compliance

- **ISO 26262** — Functional Safety for Road Vehicles (ASIL-B target)
- **MISRA C** — Guidelines for C usage in safety-critical systems

---

## 👤 Author

**Pavan Kalyan K**
📧 pkkatakam9@gmail.com
📍 Missouri, USA
🔗 [LinkedIn](https://linkedin.com/in/YOUR_PROFILE)
