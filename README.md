# Arduino-projects
# Arduino Serial Monitor Example

## 📌 Project Overview
This project demonstrates how to use the Arduino Serial Monitor to display messages from the Arduino board.

## 🎯 Objective
- Learn how to use Serial Communication.
- Understand `Serial.begin()`.
- Display text on the Serial Monitor.
- Use `Serial.println()`.

## 🛠 Components Required
- Arduino Uno
- USB Cable
- Computer with Arduino IDE

## 💻 Program Explanation

### setup()
The `setup()` function runs only once.

```cpp
Serial.begin(9600);
```

This starts serial communication at **9600 baud**.

```cpp
Serial.println("Welcome to Arduino!");
```

This prints a welcome message once when the board starts.

### loop()

```cpp
Serial.println("Hello from Arduino!");
```

Prints **Hello from Arduino!** on the Serial Monitor.

```cpp
delay(1000);
```

Waits for 1 second before printing again.

The `loop()` function repeats forever.

## ▶️ Output

```
Welcome to Arduino!
Hello from Arduino!
Hello from Arduino!
Hello from Arduino!
...
```

## 📂 Files
- `serial_monitor.ino` – Arduino program
- `README.md` – Project explanation

## 👩‍💻 Author
**Rashmitha M**
