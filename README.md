# Simple FM Transmitter with BFW92A

This project is a **small mono FM transmitter** built around the **BFW92A RF transistor**.  
It takes a stereo audio signal (L and R), mixes it to mono, and transmits it over the FM band (around 88–108 MHz).

⚠️ **Disclaimer**: This circuit is for educational and experimental use only.  
Transmitting on the FM band without a license may be restricted or illegal in your country.

---

## Circuit Diagram

![FM Transmitter Schematic](./fm_transmitter_schematic.png)  

---

## How the Circuit Works

### 1. Audio Input
- The audio comes from the **Left (L) and Right (R)** channels.  
- Two resistors mix them into a **single mono signal**.  
- A coupling capacitor passes only the AC audio signal and blocks DC, so the audio can safely enter the transistor stage.

### 2. Bias Network
- Two resistors (R4, R5) form a **voltage divider** that sets the correct operating point (bias) for the transistor’s base.  
- This ensures the transistor is not “off” or “saturated” but ready to amplify the RF oscillation.

### 3. Oscillator (LC Tank Circuit)
- The heart of the transmitter is the **LC tank circuit**:  
  - **L1 (coil)** and **C5 (variable capacitor)** decide the **carrier frequency** (in the FM broadcast band).  
  - **C6** provides feedback so the oscillation can sustain itself.  
- The transistor keeps the oscillation alive by adding energy at the right time.  
- The audio signal at the transistor’s base **slightly changes the frequency** of oscillation → this creates **frequency modulation (FM)**.

### 4. Antenna Output
- The RF signal is taken from the “hot” point of the LC tank (the junction of L1 and C5).  
- A small capacitor (C7) connects this point to the antenna, so the oscillator is not overloaded.  
- The antenna then radiates the FM signal into the air.

### 5. Power Supply
- The circuit runs from a **6V lead-acid battery**.  
- Capacitors filter the supply to keep it clean and reduce noise.  
- A diode protects against reverse polarity connection.  

---

## Improvements Implemented

- **Audio Input**
  - Increased input resistors to ~22 kΩ for proper line-level impedance.  
  - Coupling capacitor increased to 100 nF to preserve bass frequencies.  

- **Biasing**
  - Adjusted R4 (15 kΩ) and R5 (6.8 kΩ) for stable transistor operation at 6 V.  
  - Reduced emitter resistor (R6 = 620–680 Ω) for correct current flow.  

- **RF Section**
  - L1 redesigned for ~120 nH (≈5 turns of 0.8–1 mm wire on a 6 mm former).  
  - C5 set to 4–20 pF variable for tuning in the FM band.  
  - Feedback capacitor C6 optimized to 4.7–10 pF.  
  - Added C7 (2.2–5 pF) for antenna coupling.  

- **Power Supply**
  - Added 100–220 Ω resistor in series with Vcc to isolate RF from the supply.  
  - Bypass capacitors: 100 nF + 1 nF ceramic near the transistor, plus 47–100 µF electrolytic.  
  - Schottky diode + fuse for polarity protection.  

- **Optional**
  - Pre-emphasis network (75 µs) for better FM audio quality.  
  - Input trimmer (10 kΩ) for adjusting audio level and avoiding over-modulation.  

---

## Next Steps
- Add an **RF buffer stage** for improved frequency stability when driving the antenna.  
- Consider building a **stereo encoder** (L+R, L–R with 19 kHz pilot tone) for a true stereo FM transmitter.   
