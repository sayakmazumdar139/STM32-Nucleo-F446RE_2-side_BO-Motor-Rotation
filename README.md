# STM32 Dual DC BO Motor Control Using PWM, GPIO & UART (Nucleo-F446RE)

📌 Project Overview

This project demonstrates PWM-based DC motor speed and direction control using the STM32 Nucleo-F446RE development board.

The firmware is developed using HAL drivers and focuses on:

Hardware Timer (TIM2) PWM generation

GPIO-based motor direction control (H-Bridge logic)

Real-time debugging using ST-Link

Register verification via SFR view

Practical hardware validation using L298N motor driver

The system controls two BO motors with gradual speed variation and bidirectional rotation.

🎥 Project Demonstration Videos (Step-by-Step Series)

### 1️⃣ Live Demo Working 
👉[![Live Demo Working](https://img.youtube.com/vi/LVh8_5QmBsc/0.jpg)](https://youtu.be/LVh8_5QmBsc)

### 2️⃣ Project Context + STM32CubeMX Configuration  
👉[![Project Context + STM32CubeMX Configuration](https://img.youtube.com/vi/6h8yBiUqF0A/0.jpg)](https://youtu.be/6h8yBiUqF0A)

3️⃣ Code Implementation & PWM Control  👉 https://youtu.be/YfglkUXTCYQ

4️⃣ Build & Debug Process (Live)  👉  https://youtu.be/i27bujc_mCc

5️⃣ Hardware Testing with L298N Driver  👉 https://youtu.be/c-xIM9MoEZ0

Each video explains configuration, firmware logic, debugging, and real hardware validation.

🛠 Hardware Used

STM32 Nucleo-F446RE

L298N H-Bridge Motor Driver

2x BO DC Motors

12V Li-ion Battery

USB ST-Link Debug Interface

⚙️ Software & Tools

STM32CubeIDE

STM32CubeMX

HAL Drivers

ST-Link Debugger

🧠 Technical Implementation

🔹 Timer Configuration

TIM2 used in PWM Generation Mode

APB1 Timer Clock: 90 MHz

Prescaler = 89

Auto-Reload (ARR) = 1999

PWM Frequency ≈ 500 Hz

🔹 PWM Speed Control

Motor speed is varied using:

__HAL_TIM_SET_COMPARE(&htim2, TIM_CHANNEL_3, 1000);

__HAL_TIM_SET_COMPARE(&htim2, TIM_CHANNEL_3, 1500);

__HAL_TIM_SET_COMPARE(&htim2, TIM_CHANNEL_3, 2000);


Duty cycle variation controls motor speed smoothly.

🔹 Direction Control (H-Bridge Logic)

GPIO pins control direction:

HAL_GPIO_WritePin(GPIOB, GPIO_PIN_4, 0);

HAL_GPIO_WritePin(GPIOB, GPIO_PIN_5, 1);


Logic combinations:

(0,1) → Backward

(1,0) → Forward

(0,0) → Stop

🔹 Debug Validation

SFR register inspection (TIM2 → CNT, ARR, CCRx)

Verified counter increment

Confirmed CCR value change

Observed ST-Link LED behavior

Live debugging using breakpoints & step execution

📊 Functional Flow

Initialize GPIO, TIM2, UART

Start PWM on CH2 & CH3

Gradually increase duty cycle

Change direction

Repeat continuously (while loop)

🎯 Learning Outcomes

Practical PWM generation using hardware timers

Register-level debugging

Understanding APB clock & prescaler calculation

Embedded C firmware structuring

Hardware + Firmware integration

💼 Why This Project is Relevant for Embedded Firmware Roles

✔ Real hardware validation

✔ Timer-based control (not software delay PWM)

✔ Debug-level verification

✔ Clean HAL-based firmware architecture

✔ Practical H-Bridge motor control implementation

👨‍💻 Author

Sayak Mazumdar

Embedded Firmware Developer Aspirant
