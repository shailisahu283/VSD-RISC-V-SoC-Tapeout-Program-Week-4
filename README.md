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

  <img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/9c6c4023-9691-4b1a-9575-554061826e2f" />


  <img width="461" height="603" alt="image" src="https://github.com/user-attachments/assets/4f3fca5c-aa84-49b9-9736-803c6e31b3c6" />


<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/bd8734dc-41e4-4a4e-8905-de2e349e32de" />

<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/e1d5f6de-07fc-41cf-af8f-2e2980e8c1ed" />

<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/d46a71af-51d2-45fd-8786-7944e17e1ea3" />

<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/74b7d0f8-be35-49fd-84e5-ad6a64f1447f" />

<img width="1597" height="781" alt="image" src="https://github.com/user-attachments/assets/5036c853-4650-40e8-9c23-fcb8c4ba35fc" />




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

<img width="1600" height="786" alt="image" src="https://github.com/user-attachments/assets/78fe5523-a7f9-4c77-b8b1-b5e2997f1339" />

<img width="1067" height="536" alt="image" src="https://github.com/user-attachments/assets/e01d6d53-817d-4b3c-ad1a-2015596659fc" />

<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/e0f00199-2f30-4d88-8973-a5ac655ae01c" />


<img width="971" height="602" alt="image" src="https://github.com/user-attachments/assets/af13defb-0e4d-4661-9813-59d42b7f702a" />

<img width="946" height="558" alt="image" src="https://github.com/user-attachments/assets/8b78e8ea-1cb7-4a02-947b-ef559122d41d" />

<img width="945" height="563" alt="image" src="https://github.com/user-attachments/assets/4268da16-9294-4ed4-a761-b5dd61b7b30d" />

<img width="1135" height="598" alt="image" src="https://github.com/user-attachments/assets/f3995483-4b5c-4608-be13-8d9be4f9d75a" />

<img width="1342" height="612" alt="image" src="https://github.com/user-attachments/assets/58061eb4-ce0c-4474-9812-1d9900dfe693" />


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

<img width="1559" height="506" alt="image" src="https://github.com/user-attachments/assets/ce156721-8ea1-4027-b8f2-0ed0b1e19459" />

<img width="1594" height="758" alt="image" src="https://github.com/user-attachments/assets/f523d6b6-a65b-4607-a93b-1de7086776fb" />

<img width="1439" height="786" alt="image" src="https://github.com/user-attachments/assets/8f009cdb-70e7-4d10-b5eb-79b57f9d038c" />



3. **Dynamic Simulation**

   * Observe inverter response to input pulses.
   * Analyze **rise time**, **fall time**, and **propagation delay**.

### ⚙️ **Lab Outcomes**

* Create SPICE deck for inverter.
* Simulate static and dynamic responses.
* Analyze effect of increasing PMOS width on switching threshold and delay.

<img width="1229" height="578" alt="image" src="https://github.com/user-attachments/assets/0617d393-df32-48b0-a590-bf90a622d3a5" />

<img width="1339" height="753" alt="image" src="https://github.com/user-attachments/assets/f0e9d318-16af-4fe3-bdd8-7fc916195a05" />

**PMOS width is increased**
<img width="1090" height="682" alt="image" src="https://github.com/user-attachments/assets/a0d7cb65-687f-4386-8818-76f265d7a13b" />

<img width="1507" height="710" alt="image" src="https://github.com/user-attachments/assets/8bbd897a-6af7-4c22-8b25-bb99759b829e" />

<img width="959" height="483" alt="image" src="https://github.com/user-attachments/assets/ea04bbcc-7472-4ff9-a436-1dab075238e3" />

<img width="1211" height="458" alt="image" src="https://github.com/user-attachments/assets/57d569ab-9745-49f5-a0d7-dd75cea3a97a" />

<img width="1008" height="467" alt="image" src="https://github.com/user-attachments/assets/618d0a52-62fe-4de8-9cd4-3af8ef18b56c" />

<img width="1240" height="287" alt="image" src="https://github.com/user-attachments/assets/d08f46fd-b9f8-49e4-9a33-3035bedc030b" />

<img width="1287" height="723" alt="image" src="https://github.com/user-attachments/assets/da540fe3-14ed-45c2-a1df-8e1f0f2bdfe8" />


<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/beefb8db-00c8-4213-967c-07bf506fdf80" />

<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/266068f7-ba1b-498a-90a3-5fa64ae8d65f" />

<img width="614" height="587" alt="image" src="https://github.com/user-attachments/assets/364626ce-e450-4ca9-9026-2832e65a3de3" />


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

<img width="762" height="524" alt="image" src="https://github.com/user-attachments/assets/9ee6c2ca-fa76-4f2a-ac79-86fb4ad5cfb4" />

<img width="987" height="576" alt="image" src="https://github.com/user-attachments/assets/a13f8470-737a-45cb-abe6-a7ec71c450fd" />


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
  

<img width="1235" height="673" alt="image" src="https://github.com/user-attachments/assets/ab222832-408d-4476-b4ea-a63f83c99150" />

<img width="1343" height="696" alt="image" src="https://github.com/user-attachments/assets/65dc4956-5f9e-4933-b290-e75fa8e615dc" />


5. **SPICE Simulations for Variations**

   * Model transistor parameter deviations to analyze robustness.

### ⚙️ **Lab Outcomes**

* Perform **Smart SPICE** simulations for VDD variations.
* Observe effects on VTC, delay, and noise margin.
* Run device variation experiments using Sky130 models.

<img width="1493" height="770" alt="image" src="https://github.com/user-attachments/assets/de480cf3-f584-46dd-933e-7263bd1a5ebe" />

<img width="1478" height="764" alt="image" src="https://github.com/user-attachments/assets/79883bcd-bf5b-4d95-93c0-e2fcdf7ce3ff" />

<img width="1211" height="524" alt="image" src="https://github.com/user-attachments/assets/6d84b988-7f81-44c1-9794-4228de412873" />

<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/1e88498c-7719-4ef5-bb64-419e761f46d1" />

<img width="1116" height="653" alt="image" src="https://github.com/user-attachments/assets/4487cd90-19e9-499c-a1a1-bf6f7e50ee38" />

<img width="1205" height="684" alt="image" src="https://github.com/user-attachments/assets/855dde06-dd51-48fa-8f06-6dfc6b1e02e8" />

<img width="986" height="675" alt="image" src="https://github.com/user-attachments/assets/dd82218f-0263-48f2-8ce7-3b5c91a14511" />


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
