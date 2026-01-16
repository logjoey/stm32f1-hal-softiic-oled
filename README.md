# stm32f1-hal-softiic-oled
STM32F1 HAL-based software I²C OLED driver (SSD1306), supporting basic graphics and Chinese display.
# stm32f1-hal-softiic-oled

## 📌 Introduction

This project provides an **OLED display driver based on STM32F1 series microcontrollers**, implemented using the **STM32 HAL library** and **software I²C (bit-banging)**.

The driver is designed for **SSD1306-based OLED displays (128×64 resolution)** and does not rely on the hardware I²C peripheral. Instead, I²C communication is simulated using GPIO, allowing flexible pin selection and customized timing control.  

This project is suitable for learning, prototyping, and as a reusable reference for embedded applications where hardware I²C resources are limited or unavailable.
### Source and Porting

The OLED driver in this project was originally developed by **Jiangxie Technology (江协科技)** for the **0.96-inch OLED display**.  
The original driver supports character, number, Chinese text, image and graphics drawing functions with SSD1306/SSD1315 controller support. :contentReference[oaicite:0]{index=0}

This repository adapts that driver and **ports it to the STM32 HAL library**, replacing the original implementation with a HAL-compatible structure and **software I²C (GPIO bit-banging)** interface.  
The port maintains all major features while improving portability and modularity.  

Original code and assets can be downloaded from Jiangxie Technology’s download page:  
https://jiangxiekeji.com/download.html#oled :contentReference[oaicite:1]{index=1}

The original driver is free to use and modify, but the copyright remains with Jiangxie Technology.  
Please respect their original work when reusing or redistributing this code.
---

## ✨ Features
![微信图片_20260116200520_164_5](https://github.com/user-attachments/assets/c214305a-85a4-42a2-a25d-3c8e8ef7064d)

- STM32F1 series support (e.g., STM32F103)
- HAL library based implementation
- Software I²C (GPIO bit-banging)
- SSD1306 OLED support (128×64)
- ASCII character display
- Chinese character display using bitmap font tables
- Basic graphics drawing (pixel, image)
- Simple and modular code structure
- Easy to port to other STM32 series

---

## 🧩 Hardware Requirements

- STM32F1 MCU (STM32F103 recommended)
- SSD1306 OLED display module (I²C interface)
- 2 × GPIO pins for software I²C
- External pull-up resistors (if required by the OLED module)

### Example Wiring

![屏幕截图 2026-01-16 170009](https://github.com/user-attachments/assets/e733d90c-8e4d-485c-96f5-67550ad526f3)

| OLED Pin | STM32 Pin | Description |
|---------|----------|-------------|
| VCC     | 3.3V     | Power supply |
| GND     | GND      | Ground |
| SCL     | GPIOB14  | Software I²C clock |
| SDA     | GPIOB15  | Software I²C data |

---
### Character Encoding Notice

This project provides a **GB2312-encoded** version of the source files to support
Chinese character display on the OLED.

Please ensure that your Keil IDE uses the **same encoding format**, otherwise
Chinese characters may appear garbled or cause compilation errors.

You can check or modify the encoding setting in Keil as follows:

1. Click the **wrench icon** to open the Keil **Configuration** window  
2. Go to the **Editor** tab  
3. Locate the **Encoding** drop-down list  
4. Check the currently selected encoding format (recommended: **GB2312**)

## 📂 Project Structure

```text
stm32f1-hal-softiic-oled
├── Core
│   ├── Inc
│   │   ├── main.h
│   │   ├── oled.h
│   │   └── soft_iic.h
│   └── Src
│       ├── main.c
│       ├── oled.c
│       └── soft_iic.c
├── Drivers
│   └── STM32F1xx_HAL_Driver
├── Fonts
│   └── oled_font.c
├── README.md
└── LICENSE
