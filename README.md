# Arduino-projects

### 📖 Theory: What is Arduino?

**Arduino** is an open-source electronics platform based on easy-to-use hardware (a microcontroller board) and software (the Arduino IDE). It is widely used by students, hobbyists, and engineers to build electronic projects — from blinking an LED to controlling robots and IoT devices.

**Key Components of Arduino:**
- **Microcontroller (e.g., ATmega328P on Arduino Uno)** — the "brain" of the board; it runs the program (called a *sketch*) that you upload to it.
- **USB Port** — used to connect the board to a computer for programming and power.
- **Digital & Analog Pins** — used to connect sensors, LEDs, motors, and other components.
- **Power Pins** — supply voltage (5V, 3.3V, GND) to external components.

**Arduino IDE**
The Arduino IDE (Integrated Development Environment) is the software used to write, compile, and upload code (sketches) to the Arduino board. Arduino programs are written in a simplified version of C/C++.

**Structure of an Arduino Program**
Every Arduino sketch has exactly two required functions:

```cpp
void setup() {
    // runs once when the board powers on or resets
}

void loop() {
    // runs repeatedly forever after setup()
}
```

- `setup()` — used for one-time initialization, like starting serial communication or setting pin modes.
- `loop()` — contains the main logic that keeps executing again and again as long as the board is powered.

**What is Serial Communication?**
Serial communication allows the Arduino board to send and receive data to/from a computer through the USB cable, one bit at a time. This is commonly used for:
- Debugging a program (checking sensor values, variable states, etc.)
- Displaying output on the **Serial Monitor** (a tool inside the Arduino IDE)

To use it, communication must first be started at a specific **baud rate** (speed of data transfer, measured in bits per second) using `Serial.begin()`.

---

### 📌 Project Overview
This project demonstrates how to use the Arduino Serial Monitor to display messages from the Arduino board.

### 🎯 Objective
- Learn how to use Serial Communication.
- Understand `Serial.begin()`.
- Display text on the Serial Monitor.
- Use `Serial.println()`.

### 🛠 Components Required
- Arduino Uno
- USB Cable
- Computer with Arduino IDE

### 💻 Program Explanation

#### setup()
The `setup()` function runs only once.

```cpp
Serial.begin(9600);
```
This starts serial communication at **9600 baud** (9600 bits per second) — the Serial Monitor must be set to the same baud rate to read the output correctly.

```cpp
Serial.println("Welcome to Arduino!");
```
This prints a welcome message once when the board starts.

#### loop()

```cpp
Serial.println("Hello from Arduino!");
```
Prints **Hello from Arduino!** on the Serial Monitor.

```cpp
delay(1000);
```
Waits for 1 second (1000 milliseconds) before printing again.

The `loop()` function repeats forever, so this message keeps printing every second.

### ▶️ Output Welcome to Arduino!
```Hello from Arduino!
Hello from Arduino!
Hello from Arduino!
...
```
### 📂 Files
- `serial_monitor.ino` – Arduino program
- `README.md` – Project explanation.
