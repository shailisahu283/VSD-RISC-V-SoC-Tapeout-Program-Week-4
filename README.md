# VSD-RISC-V-SoC-Tapeout-Program-Week-4

## **NgspiceSky130: CMOS Fundamentals & SPICE Simulation**

---

### 📘 **Overview**

This week introduces **circuit-level design and simulation concepts** using **Ngspice with the Sky130 process technology**. The focus is on **NMOS and CMOS transistor behavior**, **drain current models**, **device operation regions**, and **inverter characteristics** (static and dynamic).

Through structured **SPICE simulations**, we explore how device parameters, geometry, and supply variations affect **performance, robustness, and reliability** of CMOS-based logic circuits — key knowledge before a **SoC tapeout**.

---

## 🧩 **Day 1 – Basics of NMOS: Id–Vds Characteristics**

### **Key Topics**

1. **Introduction to Circuit Design & SPICE Simulations**

   * Why SPICE is essential for modeling real transistor behavior considering process, voltage, and temperature (PVT) variations.
2. **NMOS Device Fundamentals**

   * Understanding **channel formation**, **strong inversion**, and **threshold voltage (Vth)**.
3. **Regions of Operation**

   * **Resistive (Linear) Region:** Small drain-source voltage; current increases linearly with Vds.
   * **Saturation Region:** Pinch-off occurs; current becomes nearly constant.
4. **SPICE Simulation Setup**

   * Creating NMOS circuits in SPICE, defining parameters, and running **Id–Vds** sweeps using Sky130 model files.

### ⚙️ **Lab Outcomes**

* Simulate **Id vs Vds** for varying gate voltages (Vgs).
* Identify **transition point** between linear and saturation region.
* Extract **threshold voltage (Vth)** using SPICE.

  <img width="1197" height="404" alt="image" src="https://github.com/user-attachments/assets/dcf832ea-c194-4228-a57b-5758fcbba05a" />


### 💬 **Concept Q&A**

**Q1. Why do we need SPICE simulations in circuit design?**
**A.** SPICE captures transistor non-idealities and second-order effects (like channel length modulation, body effect, etc.), which cannot be analyzed with simple hand calculations.

**Q2. What happens when Vds > (Vgs – Vth)?**
**A.** The MOSFET enters **saturation**, where the channel is pinched off near the drain, and the drain current (Id) becomes nearly independent of Vds.

---

## ⚡ **Day 2 – Velocity Saturation & CMOS Inverter VTC**

### **Key Topics**

1. **Velocity Saturation in Short-Channel Devices**

   * In deep submicron nodes, carrier velocity saturates at high electric fields, limiting current despite increasing Vds.
2. **Drain Current vs Gate Voltage (Id–Vgs)**

   * Comparison between long-channel and short-channel NMOS to visualize saturation effects.
3. **Introduction to CMOS Inverter**

   * Constructing an inverter with **NMOS + PMOS** pair.
   * Understanding **Voltage Transfer Characteristics (VTC)** — the relationship between input (Vin) and output (Vout).

### ⚙️ **Lab Outcomes**

* Simulate **Id–Vgs** for Sky130 NMOS/PMOS.
* Plot **VTC curve** for a CMOS inverter and identify logic thresholds.
* Analyze **switching regions**: logic low, transition, logic high.

### 💬 **Concept Q&A**

**Q1. What causes velocity saturation?**
**A.** At high electric fields, carrier drift velocity reaches a maximum (v_sat) due to scattering, limiting drain current increase.

**Q2. What is the significance of the VTC curve?**
**A.** The VTC defines how a CMOS inverter responds to varying input voltage, helping determine **noise margins** and **switching threshold**.

---

## 🔁 **Day 3 – CMOS Switching Threshold & Dynamic Simulations**

### **Key Topics**

1. **Switching Threshold (Vm)**

   * The input voltage at which Vin = Vout — defines logic transition point.
2. **Analytical Relationship of Vm**

   * Derived as a function of device width ratio:
     [
     V_m = \frac{V_{DD} + V_{tp} + \sqrt{\beta_n / \beta_p}(V_{tn})}{1 + \sqrt{\beta_n / \beta_p}}
     ]
     where (\beta = \mu C_{ox} (W/L))
3. **Dynamic Simulation**

   * Observe inverter response to input pulses.
   * Analyze **rise time**, **fall time**, and **propagation delay**.

### ⚙️ **Lab Outcomes**

* Create SPICE deck for inverter.
* Simulate static and dynamic responses.
* Analyze effect of increasing PMOS width on switching threshold and delay.

### 💬 **Concept Q&A**

**Q1. What happens if PMOS width is increased?**
**A.** Vm shifts rightward (higher) — inverter becomes more symmetric and balanced, improving noise margins.

**Q2. What does the dynamic simulation reveal?**
**A.** The real-time transition behavior of the inverter, including **charging/discharging** of load capacitance.

---

## 🔇 **Day 4 – CMOS Noise Margin Robustness**

### **Key Topics**

1. **Noise Margin Definition**

   * The measure of a circuit’s immunity to noise and signal degradation.
   * Defined as:
     [
     NM_H = V_{OH} - V_{IH}, \quad NM_L = V_{IL} - V_{OL}
     ]
2. **Importance in Digital Circuits**

   * Higher noise margin = greater signal stability.
3. **Effect of Device Sizing**

   * Variation in PMOS/NMOS dimensions alters **VTC**, thereby impacting **NMH** and **NML**.

### ⚙️ **Lab Outcomes**

* Plot and measure **Noise Margin** using SPICE.
* Compare results for different **PMOS widths** using Sky130 model.

### 💬 **Concept Q&A**

**Q1. Why is noise margin crucial in CMOS design?**
**A.** It ensures logical states are correctly interpreted despite minor voltage disturbances.

**Q2. How can we improve noise margin?**
**A.** By optimizing transistor sizing to balance rise/fall characteristics and enhance threshold symmetry.

---

## 🔋 **Day 5 – CMOS Power Supply & Device Variation Analysis**

### **Key Topics**

1. **Power Supply Variation**

   * Impact of varying VDD on inverter switching point and speed.
2. **Low Supply Voltage Design**

   * Benefits: reduced power consumption.
   * Drawback: reduced noise margin and slower switching.
3. **Device Variation Sources**

   * **Etching variation:** alters channel dimensions.
   * **Oxide thickness variation:** changes threshold voltage and transconductance.
4. **SPICE Simulations for Variations**

   * Model transistor parameter deviations to analyze robustness.

### ⚙️ **Lab Outcomes**

* Perform **Smart SPICE** simulations for VDD variations.
* Observe effects on VTC, delay, and noise margin.
* Run device variation experiments using Sky130 models.

### 💬 **Concept Q&A**

**Q1. What happens if oxide thickness increases?**
**A.** Capacitance decreases, resulting in **higher Vth** and **lower drive current**.

**Q2. Why is variation analysis critical before tapeout?**
**A.** To ensure functionality and yield across manufacturing corners (TT, FF, SS).

---

## 🌟 **Special Notes & Facts**

🔹 **SPICE (Simulation Program with Integrated Circuit Emphasis):**
A numerical engine used for analyzing transistor-level circuits by solving **Kirchhoff’s equations** iteratively.

🔹 **Sky130:**
An **open-source 130nm CMOS PDK** by Google and SkyWater Technology, enabling real silicon design and fabrication.

🔹 **Pinch-off Region:**
Occurs when the channel near the drain is depleted, restricting further current increase despite Vds rise.

🔹 **VTC Symmetry:**
A well-balanced inverter (Vm ≈ VDD/2) ensures equal noise margins for logic ‘1’ and ‘0’, improving design robustness.

🔹 **Short-Channel Effects (SCE):**
As devices shrink, electric field effects dominate, introducing velocity saturation and drain-induced barrier lowering (DIBL).

---

## 🧩 **Summary**

By the end of **Week 4**, you will:
✅ Understand MOSFET operation regions (linear, saturation, pinch-off).
✅ Run and interpret SPICE simulations for Id–Vds and Id–Vgs.
✅ Construct and analyze CMOS inverter static/dynamic behavior.
✅ Calculate and interpret noise margins.
✅ Study robustness against power and device variations using Sky130 models.
