# vasko-usb-hub

Hey everyone! This is my project for a mini **3-port USB 2.0 hub** that I designed in EasyEDA. 

At first, I was planning to add only 2 ports, but since the chip supports up to 4, I figured why not throw in an extra one. The schematic is kept super clean using Net Labels so there isn't a messy web of wires everywhere.

---
<img width="225" height="290" alt="image" src="https://github.com/user-attachments/assets/0dbaee46-a694-4f43-a97f-bec72f7c17dc" />
<img width="225" height="229" alt="copyImage" src="https://github.com/user-attachments/assets/2a1a8889-a881-40f1-9b04-36a561d7d551" />


## 🛠️ Components Used

* **Hub Controller:** `SL21A` (4-port USB 2.0 Hub Controller)[cite: 1, 8]
* **Input Port:** 1x USB Type-A Main Port (`USB-MAIN`)[cite: 1, 7]
* **Output Ports:** 3x USB Ports for peripherals (`USB1`, `USB2`, `USB3`)
* **Diode:** `B5819W` (Schottky diode for power supply protection)[cite: 9]
* **Capacitors:** 6x 10µF (0805 / 0603 SMD) for power filtering on the 5V, 3.3V, and 1.8V rails[cite: 1, 9]

---

## 📌 Pinout & Connections

### 1. Hub IC (SL21A - U1)
* **DM1 / DP1** (Pins 7, 8) ➡️ `USB1_DM` / `USB1_DP`[cite: 8]
* **DM2 / DP2** (Pins 5, 6) ➡️ `USB2_DM` / `USB2_DP`[cite: 8]
* **DM3 / DP3** (Pins 3, 4) ➡️ `USB3_DM` / `USB3_DP`[cite: 8]
* **DM4 / DP4** (Pins 1, 2) ➡️ *Unused (No Connect)*[cite: 8]
* **DM / DP** (Pins 9, 10) ➡️ `USB_IN_DM` / `USB_IN_DP` (to host PC)[cite: 8]
* **VDD5** (Pin 11) ➡️ `+5V`[cite: 8]
* **VDD33** (Pin 13) ➡️ `VDD33` (with 10µF cap to GND)[cite: 8, 9]
* **VDD18** (Pin 14) ➡️ `VDD18` (with 10µF cap to GND)[cite: 8, 9]
* **XIN / GND** (Pins 16, 12) ➡️ `GND`[cite: 8]
* **XOUT** (Pin 15) ➡️ *No Connect*[cite: 8]

---

## ⚡ Power & Filtering

1. Power comes in from the main port directly into `+5V_IN`[cite: 12].
2. It passes through diode **D1 (B5819W)** to protect the computer's USB port, converting it to the main `+5V` rail[cite: 9].
3. Each USB port and the IC power pins have a dedicated **10µF capacitor** connected to ground (`GND`) for voltage decoupling[cite: 1, 9].

---

## 💻 Design Software

The schematic was designed in **EasyEDA**. All LCSC part numbers were picked as Basic/Standard parts to keep assembly cheap if ordered through JLCPCB.

---
*This is a learning project. If you spot any bugs or have suggestions for improvements, feel free to open an issue or PR!* ✌️
