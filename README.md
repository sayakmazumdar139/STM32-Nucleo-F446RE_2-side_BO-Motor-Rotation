# STM32 Dual DC BO Motor Control Using PWM, GPIO & UART (Nucleo-F446RE)

## 🔎 Executive Summary

A dual DC motor control system implemented on STM32 Nucleo-F446RE using hardware timer-based PWM.  
Demonstrates bidirectional motor control, smooth duty-cycle variation, register-level debugging, and real hardware validation using L298N driver.

Focus Areas:
- Hardware Timer (TIM2) PWM generation
- GPIO-based H-Bridge control
- Debug verification via SFR inspection
- Embedded C firmware structuring


## 📌 Project Overview

This project demonstrates PWM-based DC motor speed and direction control using the STM32 Nucleo-F446RE development board.

The firmware is developed using HAL drivers and focuses on:

♦️Hardware Timer (TIM2) PWM generation

♦️GPIO-based motor direction control (H-Bridge logic)

♦️Real-time debugging using ST-Link

♦️Register verification via SFR view

♦️Practical hardware validation using L298N motor driver

The system controls two DC BO motors with smooth speed variation and bidirectional rotation using hardware-timer based PWM.


## 🚀 Key Features

- Dual DC motor control using hardware PWM
  
- Bidirectional rotation via H-Bridge logic
 
- Gradual duty-cycle based speed variation
  
- Real-time debugging using ST-Link
  
- Register-level verification (TIM2 → CNT, ARR, CCR)


## 🧩 System Architecture

STM32 (TIM2 PWM) → L298N Driver → DC Motors

                ↑
             GPIO (Direction)


## 🎥 Project Demonstration Videos (Step-by-Step Series)

### 1️⃣ Live Demo Working 
👉[![Live Demo Working](https://img.youtube.com/vi/LVh8_5QmBsc/0.jpg)](https://youtu.be/LVh8_5QmBsc)

### 2️⃣ Project Context + STM32CubeMX Configuration  
👉[![Project Context + STM32CubeMX Configuration](https://img.youtube.com/vi/6h8yBiUqF0A/0.jpg)](https://youtu.be/6h8yBiUqF0A)

### 3️⃣ Code Implementation & PWM Control
👉 [![Code Implementation & PWM Control](https://img.youtube.com/vi/YfglkUXTCYQ/0.jpg)](https://youtu.be/YfglkUXTCYQ)

### 4️⃣ Build & Debug Process (Live)
👉  [![Build & Debug Process (Live)](https://img.youtube.com/vi/i27bujc_mCc/0.jpg)](https://youtu.be/i27bujc_mCc)

### 5️⃣ Hardware Testing with L298N Driver
👉 [![Hardware Testing with L298N Driver](https://img.youtube.com/vi/c-xIM9MoEZ0/0.jpg)](https://youtu.be/c-xIM9MoEZ0)

Each video explains configuration, firmware logic, debugging, and real hardware validation.

## 🛠 Hardware Used

✔️STM32 Nucleo-F446RE Dev. Board

✔️L298N H-Bridge Motor Driver

✔️2x BO DC Motors with wheels

✔️12V Li-ion Battery with ON-OFF Switch

✔️Jumper Wires

✔️USB ST-Link Debug Interface(Probe)

✔️PC/Laptop


## 🔌 Pin Configuration

| Function | STM32 Pin | Description |
|----------|-----------|-------------|
| PWM CH2  | PA1       | Motor 2 Speed |
| PWM CH3  | PB10      | Motor 1 Speed |
| GPIO     | PB4       | Motor 1 Direction Control |
| GPIO     | PB5       | Motor 1 Direction Control |
| GPIO     | PA4       | Motor 2 Direction Control |
| GPIO     | PB0       | Motor 2 Direction Control |


## ⚙️ Software & Tools

☑️STM32CubeMX

☑️STM32CubeIDE

☑️STM32CubeProgrammer

☑️HAL Drivers

☑️ST-Link Debugger


## 🧠 Technical Implementation

🔹 Timer Configuration

◻️ TIM2 used in PWM Generation Mode

◻️ APB1 Timer Clock: 90 MHz

◻️ Prescaler = 89

◻️ Auto-Reload (ARR) = 1999

◻️ PWM Frequency ≈ 500 Hz


🔹 PWM Speed Control

◻️ Motor_1 speed is varied using:

__HAL_TIM_SET_COMPARE(&htim2, TIM_CHANNEL_3, 1000);

__HAL_TIM_SET_COMPARE(&htim2, TIM_CHANNEL_3, 1500);
 
__HAL_TIM_SET_COMPARE(&htim2, TIM_CHANNEL_3, 2000);

◻️ Duty cycle variation controls motor speed smoothly.


🔹 Direction Control (H-Bridge Logic)

▶️  GPIO pins control direction:

HAL_GPIO_WritePin(GPIOB, GPIO_PIN_4, 0);

HAL_GPIO_WritePin(GPIOB, GPIO_PIN_5, 1);


✅ Logic combinations:

(0,1) → Backward

(1,0) → Forward

(0,0) → Stop


🔹 Debug Validation

🔸 SFR register inspection (TIM2 → CNT, ARR, CCRx)
 
🔸 Verified counter increment

🔸 Confirmed CCR value change

🔸 Observed ST-Link LED behavior

🔸 Live debugging using breakpoints & step execution

## 🧠 Design Decisions

- Used hardware timer PWM instead of software delay for stable frequency generation.
  
- Selected 500 Hz PWM frequency for smooth motor operation.
  
- Verified timer operation using CNT register observation.
  
- Implemented incremental duty-cycle ramping for visible speed transition.


## 📂 Project Structure

/Core  
/Drivers  
/Src/main.c  
/Inc  

## 📄 Firmware Implementation (main.c Overview)

The main firmware logic resides in `main.c`, which includes:

- Peripheral initialization 👉 (GPIO, TIM2, UART)
- PWM start configuration using 👉 HAL_TIM_PWM_Start()
- Direction control using 👉 HAL_GPIO_WritePin()
- Duty cycle adjustment via 👉 __HAL_TIM_SET_COMPARE()
- Infinite loop control logic 👉 (while(1))


## 📊 Functional Flow

✅ Initialize GPIO, TIM2, UART

✅ Start PWM on CH2 & CH3

✅ Gradually increase duty cycle

✅ Change direction

✅ Repeat continuously (while loop)


## 🎯 Learning Outcomes

♦️ Practical PWM generation using hardware timers

♦️ Register-level debugging

♦️ Understanding APB clock & prescaler calculation

♦️ Embedded C firmware structuring

♦️ Hardware + Firmware integration


## 🔮 Future Improvements

- Implement PWM control using DMA
  
- Add UART-based speed command interface
  
- Integrate encoder feedback for closed-loop control
  
- Port to FreeRTOS-based task scheduling


## 💼 Why This Project is Relevant for Embedded Firmware Roles

✔ Real hardware validation

✔ Timer-based control (not software delay PWM)

✔ Debug-level verification

✔ Clean HAL-based firmware architecture

✔ Practical H-Bridge motor control implementation


## 👨‍💻 Author

Sayak Mazumdar 

Embedded Firmware Developer Aspirant
