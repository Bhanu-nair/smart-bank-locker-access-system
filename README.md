# 🔐 Smart Bank Locker Access System

## Two-Level Security System Using RFID and Password Authentication with LPC2129 ARM7 Microcontroller and UART Communication
An Embedded C-based Smart Bank Locker Access System using LPC2129 ARM7, featuring two-level authentication with EM-18 RFID and keypad password verification, UART communication, LCD interfacing, and motor-based locker control.
<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/2c07796f-2ecc-42fb-a2f6-598a1c965214" />
## 📌 1. Project Overview

**Smart Bank Locker Access System** is an embedded security system designed to provide secure locker access through two-level authentication using RFID and password verification.

The system integrates **EM-18 RFID authentication, keypad-based password verification, UART communication, LCD monitoring, LED and buzzer indications, and DC motor-based locker control** using the **LPC2129 ARM7 microcontroller**.

The project demonstrates the practical implementation of:

- Embedded C Programming
- ARM7 LPC2129 Microcontroller
- UART Communication (UART0)
- RFID Interfacing (EM-18)
- Password-Based Authentication
- 4×4 Keypad Interfacing
- 16×2 LCD Interfacing
- DC Motor Control
- GPIO Configuration and Control
- LED Interfacing
- Hardware–Software Integration
- Embedded System Design and Testing
## 📝 2. Abstract

Security and controlled access are essential requirements in banking environments, particularly for protecting valuable assets stored in lockers. Traditional access methods may have limitations in providing multiple levels of authentication and reliable access monitoring.

**Smart Bank Locker Access System** is an embedded security system developed using the **LPC2129 ARM7 microcontroller** to provide two-level authentication through RFID card verification and password confirmation.

An **EM-18 RFID reader** detects the RFID card and transmits its identification data to the LPC2129 microcontroller through **UART0 communication**. The controller compares the received card ID with a predefined authorized ID to verify the user's identity.

Upon successful RFID authentication, the system prompts the user to enter a password using a **4×4 matrix keypad**. The entered password is compared with a predefined password, with a maximum of three attempts allowed for authentication.

When both authentication levels are successful, the **DC motor operates to unlock the locker**, while the **16×2 LCD displays the access status**. An LED and buzzer provide visual and audio indications for successful and unsuccessful authentication.

The project demonstrates the practical implementation of a **two-level embedded access-control system using ARM7 microcontroller programming, UART0 communication, peripheral interfacing, and hardware–software integration**.

## 🎯 3. Objectives

- Implement RFID-based user authentication using the EM-18 RFID reader.
- Receive and process RFID data through UART0 communication.
- Verify scanned RFID card IDs against a predefined authorized ID.
- Implement password-based authentication using a 4×4 matrix keypad.
- Provide two-level security through RFID verification and password confirmation.
- Limit password authentication to a maximum of three attempts.
- Control locker access using a DC motor based on authentication results.
- Display authentication status and system messages on a 16×2 LCD.
- Display system status and authentication messages through the Flash Magic Terminal Window using UART0 communication.
- Provide visual  alerts using LED  indications.
- Develop the embedded system using Embedded C on the LPC2129 ARM7 microcontroller.
- Demonstrate hardware–software integration through peripheral interfacing and system testing.

- 🏗️ 4. System Architecture

        ┌─────────────────────┐
        │      RFID CARD      │
        └──────────┬──────────┘
                   │
                   ▼
        ┌─────────────────────┐          ┌─────────────────────┐
        │     RFID READER     │          │        KEYPAD       │
        └──────────┬──────────┘          └──────────┬──────────┘
                   │ UART0                          │ GPIO
                   ▼                                ▼
        ┌──────────────────────────────────────────────────┐
        │                  LPC2129 (ARM7)                  │
        │                                                  │
        │   - RFID card ID verification                    │
        │   - Keypad password check                        │
        │   - Lockout after 3 wrong attempts               │
        │   - Peripheral drivers (Embedded C)              │
        └────────────────────────┬─────────────────────────┘
                                 │
                                 ▼
        ┌──────────────────────────────────────────────────┐
        │              Motor (Lock) | LCD | LED            │
        └──────────────────────────────────────────────────┘
## 🔧 5. Hardware Components

### Microcontroller
- LPC2129 ARM7TDMI-S
- ARM7 microcontroller
- UART0 interface
- GPIO

### RFID Section
- RFID Reader (UART0)
- RFID Card / RFID Tag

### Input
- Keypad (password entry)

### Display and Indication
- LCD
- LED

### Locker Control
- Motor (locker lock)

### Other Components
- Power Supply
- Connecting Wires
- Development Board

---

## 💻 6. Software and Development Tools

- Embedded C
- Keil µVision
- Proteus (circuit simulation)
- ARM7 LPC2129 Development Environment

---

## ⚙️ 7. Working Principle

### Step 1 — RFID Scanning
The RFID card is placed near the RFID reader.

The reader detects the card and obtains its unique identification value.

The RFID data is transferred to the LPC2129 through UART0.

```
RFID Card
   ↓
RFID Reader
   ↓
UART0
   ↓
LPC2129
```

### Step 2 — RFID Authentication
The LPC2129 receives the card ID through UART0.

The received ID is compared with the stored authorized card ID.

```
RFID ID
   ↓
LPC2129
   ↓
Compare with Authorized ID
   ↓
┌───────────────┐
│    Match ?    │
└───────┬───────┘
        │
   ┌────┴────┐
   │         │
  YES        NO
   │         │
   ▼         ▼
 VALID     INVALID
```

### Step 3 — Password Entry
Only after a valid RFID card is detected, the user enters the password on the keypad.

```
Valid RFID Card
      ↓
Keypad Password Entry
      ↓
LPC2129
```

### Step 4 — Password Authentication
The LPC2129 compares the entered password with the stored password.

```
Entered Password
      ↓
LPC2129
      ↓
Compare with Stored Password
      ↓
┌───────────────┐
│    Match ?    │
└───────┬───────┘
        │
   ┌────┴────┐
   │         │
  YES        NO
   │         │
   ▼         ▼
 VALID     WRONG
 PASSWORD  PASSWORD
```

### Step 5 — Locker Control
The motor unlocks the locker only when both the RFID card ID and the password are valid.

```
Valid RFID + Valid Password
            ↓
         LPC2129
            ↓
          Motor
            ↓
     Locker Unlocked
```

### Step 6 — LCD Display
The LCD shows the access status.

For valid RFID and password:
```
ACCESS GRANTED
```

For invalid RFID or wrong password:
```
ACCESS DENIED
```

### Step 7 — Indication
The LED indicates the granted and denied states along with the LCD message.

```
Access Result
      ↓
   LPC2129
      ↓
LCD → ACCESS GRANTED / ACCESS DENIED
      ↓
     LED
```

### Step 8 — Lockout after 3 Wrong Attempts
The LPC2129 counts wrong password attempts. After 3 wrong attempts, the session ends and unauthorized access is blocked.

```
Wrong Password
      ↓
Attempt Count + 1
      ↓
┌───────────────┐
│ Count = 3 ?   │
└───────┬───────┘
        │
   ┌────┴────┐
   │         │
  NO        YES
   │         │
   ▼         ▼
Try Again  Session Ends
```

### Step 9 — Complete System Operation
The complete system works as a two-factor authentication locker: RFID card first, then password.

```
          RFID CARD
              ↓
       ┌─────────────┐
       │ RFID READER │
       └──────┬──────┘
              │ UART0
              ▼
       ┌─────────────┐        ┌─────────────┐
       │   LPC2129   │◄───────│   KEYPAD    │
       │    ARM7     │        └─────────────┘
       └──────┬──────┘
              │
              ▼
     Motor | LCD | LED
```

**Valid Flow**
```
VALID RFID
    ↓
Enter Password
    ↓
VALID PASSWORD
    ↓
Locker Unlocks
    ↓
LCD Shows ACCESS GRANTED
```

**Invalid Flow**
```
INVALID RFID or WRONG PASSWORD
    ↓
Access Denied
    ↓
Locker Remains Locked
    ↓
LCD Shows ACCESS DENIED
    ↓
After 3 Wrong Attempts → Session Ends
```

---

## ✅ 8. Advantages

- Two-factor authentication using RFID card and password.
- Prevents unauthorized access to the locker.
- Session ends after 3 wrong password attempts.
- Motor provides automatic locker unlocking.
- LCD displays access status clearly.
- LED provides visual indication of access result.
- Simple, low-cost design on an ARM7 microcontroller.
- Modular peripheral drivers written in Embedded C make the system easy to modify.

---

## 🎯 9. Applications

- Bank locker access control
- Vault and safe security
- Secure document storage
- Restricted-area access control
- Secure laboratory access
- Office and school cabinet security
- Hostel and warehouse storage security
- Smart home security systems

 ## 👤 Author

Bhanu A Nair

B.Tech Electronics and Communication Engineering Graduate (Minor in Computer Science)


Embedded Systems Trainee, Vector India Institute 

- LinkedIn: www.linkedin.com/in/bhanu-a-nair
- GitHub:   https://github.com/Bhanu-nair
- Email :  bhanuanair23@gmail.com
