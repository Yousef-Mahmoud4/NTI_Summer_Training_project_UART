# NTI_Summer_Training_project_UART
# UART Design in Verilog

## Introduction

This project presents a **UART (Universal Asynchronous Receiver/Transmitter)** implementation using Verilog.
The design is composed of the following building blocks:

* **Baud Rate Generator** – produces timing signals for data synchronization
* **UART Receiver (RX)** – captures incoming serial data and converts it to parallel format
* **UART Transmitter (TX)** – sends parallel data as a serial stream with proper framing
* **Verification Testbenches** – ensure functional correctness at every stage

The development process was carried out incrementally to make debugging and validation more efficient.

---

##  Development Stages

### Baud Rate Generator

* **Role**: Generates baud ticks and enable pulses that align the timing between TX and RX.
* **Why first**: Since accurate timing is essential in UART, this module was created and tested before implementing the main logic.
* **Testing**: A standalone testbench was prepared to validate correct baud tick generation.

---

### UART Receiver (RX)

* **Role**: Detects the start bit, samples incoming bits, and reconstructs an 8-bit parallel word.
* **Features**:

  * Start bit recognition
  * Serial-to-parallel shifting
  * Stop bit checking with error detection
  * Control/status signals: `done`, `busy`, `err`
* **Testing**: Verified byte reception, detection of framing errors, and synchronization with the baud generator.

---

### UART Transmitter (TX)

* **Role**: Sends data from an 8-bit parallel register to the serial line, framed with start and stop bits.
* **Features**:

  * Generates correct start and stop bits
  * Handles ongoing transmission with a `busy` signal
  * Ensures proper sequencing of outgoing bits
* **Testing**: Confirmed correct output timing, byte accuracy, and back-to-back transmissions.

---

### Enhanced Testbenches

Once the RX and TX modules passed basic checks, the verification environment was extended to:

* Run tests on a variety of data patterns
* Perform **loopback tests** (TX connected to RX)
* Validate continuous data transfers
* Trigger and observe framing error conditions
* Ensure stable, robust operation under multiple scenarios

---

## Summary

The project followed a structured path: starting with the **Baud Generator**, then building the **Receiver**, the **Transmitter**, and finally enhancing the **testbenches**.
This step-by-step approach made the design process modular, reliable, and easier to debug.

---
