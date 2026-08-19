# 🚀 Cyclic Redundancy Check (CRC) Generator & Interactive Visualizer

A modern, interactive web-based tool for calculating **Cyclic Redundancy Checks (CRC)**, error detection, and visualizing step-by-step **Modulo-2 Binary Long Division**.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/TailwindCSS-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)

---

## 📌 Table of Contents
- [Overview](#-overview)
- [Key Features](#-key-features)
- [How CRC Works (Theory & Math)](#-how-crc-works-theory--math)
- [Interactive Long-Division Visualizer](#-interactive-long-division-visualizer)
- [Getting Started](#-getting-started)
- [Project Structure](#-project-structure)
- [Author](#-author)
- [License](#-license)

---

## 🌟 Overview

The **Cyclic Redundancy Check (CRC)** is a widely used error-detecting code in digital communication and storage systems (e.g., Ethernet, Wi-Fi, USB, PNG, ZIP). 

This project bridges the gap between low-level algorithm code (Java) and an intuitive, visual educational interface. It allows students, engineers, and developers to input any custom **Data Bit Stream** and **Generator Polynomial** to see the full encoding pipeline, receiver-side verification, and textbook-style modulo-2 long-division step-by-step.

---

## ✨ Key Features

- **Dynamic Modulo-2 Arithmetic**: Implements standard binary polynomial division (GF(2) arithmetic).
- **Textbook Long-Division Diagram**: Aligned column-by-column division bracket with dynamic quotient generation, step-by-step XORing, and vertical drop lines.
- **Interactive Stepper Controls**: Play, pause, step forward, and step back through individual bit operations.
- **Interactive Receiver & Error Injection**:
  - Test simulated transmissions over noisy channels.
  - Click on any bit in the transmitted codeword to flip it (`0 ⇄ 1`).
  - Real-time receiver evaluation confirms whether the packet is accepted or corrupted.
- **Standard Polynomial Presets**: Quick one-click selection for CRC-4, CRC-5-USB, CRC-8, and standard academic test vectors.
- **Responsive & Modern UI**: Built with Tailwind CSS, supporting dark mode aesthetics, clean cards, and responsive layout.

---

## 🔬 How CRC Works (Theory & Math)

CRC treats binary bit sequences as coefficients of polynomials over the Galois Field of two elements, $\text{GF}(2)$:

1. **Zero Appending**: If the Generator Polynomial $G(x)$ has degree $r$ (length $n = r + 1$), append $r$ zeros to the original Data Stream $D(x)$.
2. **Modulo-2 Division**: Perform long division of the zero-appended data stream $D(x) \cdot x^r$ by $G(x)$ using XOR arithmetic:
   - $0 \oplus 0 = 0$
   - $0 \oplus 1 = 1$
   - $1 \oplus 0 = 1$
   - $1 \oplus 1 = 0$
   *(Addition and subtraction in $\text{GF}(2)$ are identical to the XOR operation)*
3. **Codeword Formation**: The resulting remainder $R(x)$ of length $r$ is appended to the original Data Stream to form the transmitted codeword:
   $$\text{Transmitted Data} = D(x) \cdot x^r + R(x)$$
4. **Receiver Verification**: The receiver divides the received codeword by the same Generator Polynomial $G(x)$. 
   - If **Remainder $= 0$**: No detectable transmission errors occurred.
   - If **Remainder $\neq 0$**: Transmission error detected; packet discarded/retransmitted.

---

## 📐 Interactive Long-Division Visualizer

The built-in division engine renders the exact layout taught in computer networking and communication courses:

```text
                  1 1 0 0 0 0 1 0 1 0   <-- Quotient
       +-----------------------------
10011  |  1 1 0 1 0 1 1 0 1 1 1 1 0     <-- Dividend (Data + Zeros)
       ^  1 0 0 1 1 | | | | | | | |
       -------------| | | | | | | |
          1 0 0 1 1 | | | | | | | |     <-- Step Remainder + Brought Down Bit
          1 0 0 1 1 | | | | | | | |
          ----------| | | | | | | |
            0 0 0 0 1 | | | | | | |
            0 0 0 0 0 | | | | | | |
            ----------| | | | | | |
                   ...
                      0 0 0 0 0         <-- Final Remainder (CRC)
```
---
## 🚀 Getting Started

Follow these simple steps to run the project locally on your machine.

### Prerequisites

* Any modern web browser (e.g., Google Chrome, Mozilla Firefox, Microsoft Edge, Safari)
* Git (optional, for cloning)

### Installation & Setup

1. **Clone the repository** (or download the ZIP file):
   ```bash
   git clone [https://github.com/your-username/crc-visualizer.git](https://github.com/your-username/crc-visualizer.git)

---
## 📂 Project Structure

├── index.html        # Main web application, interactive UI, and division engine
└── README.md         # Documentation and project overview

---

## 👤 Author

Made by Anant Patil.

---

