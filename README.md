# Arduino-projects

## 📘 Section 1: Fundamentals

---

### 1. What is Arduino?

**Arduino** is an open-source electronics platform based on easy-to-use hardware (a microcontroller board) and software (the Arduino IDE). It is widely used by students, hobbyists, and engineers to build electronic projects — from blinking an LED to controlling robots and IoT devices.

**Key Components of Arduino:**
- **Microcontroller (e.g., ATmega328P on Arduino Uno)** — the "brain" of the board; it runs the program (called a *sketch*) that you upload to it.
- **USB Port** — used to connect the board to a computer for programming and power.
- **Digital & Analog Pins** — used to connect sensors, LEDs, motors, and other components.
- **Power Pins** — supply voltage (5V, 3.3V, GND) to external components.

**Why Arduino is popular:**
- Beginner-friendly, simplified C/C++ programming
- Low cost and widely available
- Huge community support and ready-made libraries
- Works with thousands of sensors and modules

---

### 2. Basic Electronics Concepts

Before writing any Arduino code, it helps to understand a few core electrical concepts.

**Voltage (V)**
The "push" or pressure that moves electric charge through a circuit. Measured in **Volts (V)**. Arduino boards typically operate at **5V** or **3.3V**.

**Current (I)**
The rate of flow of electric charge through a wire or component. Measured in **Amperes (A)**.

**Resistance (R)**
Opposition to the flow of current. Measured in **Ohms (Ω)**. Resistors are used to limit current in a circuit (e.g., to protect an LED from burning out).

**Ohm's Law**
Relates voltage, current, and resistance: V=IxR
- `V` = Voltage (Volts)
- `I` = Current (Amps)
- `R` = Resistance (Ohms)

Example: If a circuit has 5V and 500Ω resistance, the current flowing is:
I=VxR=5/500=0.01A(10mA)

 **AC vs DC**
- **AC (Alternating Current)** — current that changes direction periodically (used in household power supply).
- **DC (Direct Current)** — current that flows in one constant direction (used by Arduino, batteries, and most electronics).

**What is a Circuit?**
A circuit is a closed loop through which electric current can flow.
- **Closed Circuit** — a complete path; current flows (e.g., LED lights up).
- **Open Circuit** — a broken path; current cannot flow (e.g., a switch turned off).

---

### 3. Introduction to the Breadboard

A **breadboard** is a reusable board used to build and test circuits without soldering.

**Breadboard Layout:**
- **Terminal Strips (middle rows)** — each row of 5 holes (labeled a-e or f-j) is electrically connected internally. Components placed in the same row are connected to each other.
- **Power Rails (side columns)** — the two outer columns marked `+` (red) and `-` (blue) run the full length of the board and are used to distribute power (VCC and GND) to multiple components.

**Key Rule:**
Rows are connected **horizontally** (within the same group of 5), and power rails are connected **vertically** (along the entire strip) — the two halves of the board (top and bottom) are usually *not* connected to each other in the middle.

---

### 4. Arduino Board Anatomy (Arduino Uno)

| Component | Description |
|-----------|-------------|
| **Digital Pins (0-13)** | Can be set as INPUT or OUTPUT; read/write HIGH (5V) or LOW (0V) signals |
| **PWM Pins (marked with ~)** | Digital pins that can simulate analog output using Pulse Width Modulation (e.g., pins 3, 5, 6, 9, 10, 11) |
| **Analog Input Pins (A0-A5)** | Read varying voltage signals (0-5V) from sensors like potentiometers |
| **5V Pin** | Supplies regulated 5V to external components |
| **3.3V Pin** | Supplies regulated 3.3V for low-voltage components |
| **GND Pins** | Ground — common reference point (0V) for the circuit |
| **VIN Pin** | Used to supply external power (7-12V) to the board |
| **USB Port** | Used for programming the board and powering it via computer |
| **Reset Button** | Restarts the program currently on the board |

**Power Options:**
- Via USB cable (5V, from computer)
- Via VIN pin or barrel jack (external adapter, 7-12V recommended)

---

### 5. Installing Arduino IDE

**Steps:**
1. Go to the official Arduino website: [https://www.arduino.cc/en/software](https://www.arduino.cc/en/software)
2. Download the IDE version for your operating system (Windows/Mac/Linux)
3. Install and open the Arduino IDE
4. Connect your Arduino board to the computer using a USB cable
5. Go to **Tools > Board** and select your board (e.g., "Arduino Uno")
6. Go to **Tools > Port** and select the correct COM port your board is connected to
7. You're now ready to write and upload code

---

### 6. Structure of an Arduino Sketch

Every Arduino program (called a **sketch**) has two required functions:

```cpp
void setup() {
    // Runs once when the board powers on or is reset
    // Used for initialization (e.g., Serial.begin(), pinMode())
}

void loop() {
    // Runs repeatedly, forever, after setup() finishes
    // Contains the main logic of the program
}
```

**Key Syntax Rules:**
- Every statement ends with a semicolon `;`
- Code blocks are enclosed in curly braces `{ }`
- Comments are ignored by the compiler and used for notes:
```cpp
  // This is a single-line comment
  /* This is a
     multi-line comment */
```

**Example — Minimal Sketch:**
```cpp
void setup() {
    // runs once
}

void loop() {
    // runs forever
}
```
This is the smallest valid Arduino program — it does nothing, but it will compile and upload
successfully.

---

## 📘 Section 2: Core Programming Concepts

---

### 7. Variables & Data Types

A **variable** is a named storage location in memory that holds a value which can change during program execution.

**Syntax:**
```cpp
data_type variable_name = value;
```

**Common Data Types in Arduino (C++):**

| Data Type | Description | Example |
|-----------|-------------|---------|
| `int` | Whole numbers (no decimals) | `int age = 25;` |
| `float` | Decimal numbers | `float temp = 36.6;` |
| `bool` | True or false only | `bool ledState = true;` |
| `char` | A single character | `char grade = 'A';` |
| `String` | A sequence of characters (text) | `String name = "Arduino";` |

**Example:**
```cpp
void setup() {
    Serial.begin(9600);
    int sensorValue = 512;
    float voltage = 2.5;
    bool isOn = true;
    char symbol = 'X';
    String message = "Hello Arduino";

    Serial.println(sensorValue);
    Serial.println(voltage);
    Serial.println(isOn);
    Serial.println(symbol);
    Serial.println(message);
}

void loop() {
}
```

---

### 8. Constants

A **constant** is a value that cannot be changed once defined. Used for values that stay fixed throughout the program (e.g., a pin number).

**Two ways to define constants:**

**1. Using `const` keyword:**
```cpp
const int ledPin = 13;
```

**2. Using `#define` (preprocessor directive):**
```cpp
#define LED_PIN 13
```

**Difference:**
- `const` creates a typed variable that the compiler checks for type safety.
- `#define` is a simple text replacement done before compilation — no type checking.

`const` is generally preferred in modern Arduino programming.

---

### 9. Operators

**Arithmetic Operators**
| Operator | Meaning | Example (a=10, b=3) | Result |
|----------|---------|----------------------|--------|
| `+` | Addition | a + b | 13 |
| `-` | Subtraction | a - b | 7 |
| `*` | Multiplication | a * b | 30 |
| `/` | Division | a / b | 3 |
| `%` | Modulus (remainder) | a % b | 1 |

**Relational Operators** (used in conditions, return true/false)
| Operator | Meaning |
|----------|---------|
| `==` | Equal to |
| `!=` | Not equal to |
| `>` | Greater than |
| `<` | Less than |
| `>=` | Greater than or equal to |
| `<=` | Less than or equal to |

**Logical Operators**
| Operator | Meaning |
|----------|---------|
| `&&` | Logical AND |
| `\|\|` | Logical OR |
| `!` | Logical NOT |

---

### 10. Conditional Statements

Used to make decisions in code — run different code blocks based on a condition.

**if statement:**
```cpp
if (condition) {
    // runs if condition is true
}
```

**if-else statement:**
```cpp
if (temperature > 30) {
    Serial.println("It's hot");
} else {
    Serial.println("It's cool");
}
```

**if-else if-else (multiple conditions):**
```cpp
if (sensorValue > 700) {
    Serial.println("Bright");
} else if (sensorValue > 300) {
    Serial.println("Medium");
} else {
    Serial.println("Dark");
}
```

**switch statement (alternative to multiple if-else):**
```cpp
switch (day) {
    case 1:
        Serial.println("Monday");
        break;
    case 2:
        Serial.println("Tuesday");
        break;
    default:
        Serial.println("Other day");
        break;
}
```

---

### 11. Loops

Loops repeat a block of code multiple times.

**for loop** — used when the number of repetitions is known:
```cpp
for (int i = 0; i < 5; i++) {
    Serial.println(i);
}
```
- `int i = 0` — initialization (runs once)
- `i < 5` — condition (checked before each loop)
- `i++` — increment (runs after each loop)

**while loop** — repeats as long as a condition is true:
```cpp
int i = 0;
while (i < 5) {
    Serial.println(i);
    i++;
}
```

**do-while loop** — runs the code at least once, then checks the condition:
```cpp
int i = 0;
do {
    Serial.println(i);
    i++;
} while (i < 5);
```

---

### 12. Functions

A **function** is a reusable block of code that performs a specific task.

**Built-in functions** you've already used: `Serial.begin()`, `Serial.println()`, `delay()`

**Writing a custom function:**
```cpp
return_type function_name(parameters) {
    // code
    return value; // if return_type is not void
}
```

**Example:**
```cpp
int addNumbers(int a, int b) {
    int sum = a + b;
    return sum;
}

void setup() {
    Serial.begin(9600);
    int result = addNumbers(5, 3);
    Serial.println(result); // prints 8
}

void loop() {
}
```

- `int` before the function name means it returns an integer.
- `void` means the function doesn't return anything.

---

### 13. Arrays

An **array** stores multiple values of the same data type under a single variable name.

**Syntax:**
```cpp
data_type array_name[size] = {value1, value2, value3};
```

**Example:**
```cpp
int ledPins[3] = {9, 10, 11};

void setup() {
    for (int i = 0; i < 3; i++) {
        pinMode(ledPins[i], OUTPUT);
    }
}

void loop() {
}
```

- `ledPins[0]` accesses the first element (9)
- Array indexing starts at **0**, not 1
- Arrays are useful for controlling multiple similar components (like several LEDs) using a loop

---
