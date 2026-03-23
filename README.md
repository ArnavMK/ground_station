---
# Glacadóir: Handheld Rocketry Ground Station

**3D Render:**

[Insert your 3D CAD render here]

**PCB Layout (Rev 1.2):**

[Insert your KiCad 2D or 3D view here]

### What is this project?

Glacadóir is a custom handheld telemetry terminal designed to receive, process, and visualize real-time data from high-power rockets. It serves as the primary interface for the **ULAS HiPR** team during the **Mach 2026** and **Euroc 2026** competition.

This board acts as a portable "command center," featuring:

- **Adafruit KB2040 (RP2040):** The brain handling high-speed data processing.
- **Radio expansion cartridges:** A game boy style cartridge system that enables the ground station to adapt to different radio protocols like UART (Eggfinder RX) and SPI (LoRa)
- **IPS Display:** Real-time visualization of flight curves and GPS coordinates.
- **Power Management:** A dual-input "Ideal Diode" with Micro Lipo battery charger system for seamless USB/Battery switching. (also data transfer).

### How to use it?

Glacadóir is designed for field portability. It connects to a standard 868MHz SMA antenna and is powered by a single-cell LiPo battery.

1. **Telemetry:** Receives flight data via the radio protocol attached and displays it on the internal IPS screen.
2. **Interaction:** A 5-button navigational matrix allows the user to switch between data screens (velocity, altitude, GPS).
3. **Expansion:** Features a dedicated UART/SPI expansion port to connect external modules like an Eggtimer or secondary radio adapters.
4. **Charging:** Integrated USB-C charging allows for field-topping while the station remains active.

### Why I made it

This project was made for the ULAS HiPR’s ground station needs. 

---

### Bill of Materials (BOM) - Rev 1.2

| Part | Amount | Link | Cost |
| --- | --- | --- | --- |
| MicroLipo charger | 1 | [Link](https://www.digikey.ie/en/products/detail/adafruit-industries-llc/1904/5054545) | 6.95 |
| Display | 1 | [Link](https://www.digikey.ie/en/products/detail/adafruit-industries-llc/5206/15204095) | 17.5 |
| Main Power Switch | 1 | [Link](https://www.digikey.com/en/products/detail/c-k/OS102011MA1QN1/1981430) | 0.65 |
|  |  |  |  |
| Tactile Switches | 6 | [Link](https://www.digikey.com/en/products/detail/e-switch/TL3301AF160QG/378993) | 0.39 |
| SP0503BAHT ESD diode array | 1 | [Link](https://www.digikey.com/en/products/detail/littelfuse-inc/SP0503BAHTG/1154308) | 0.53 |
| 0805 resistor package (10k) | 11 | [Link](https://www.digikey.com/en/products/detail/bourns-inc/CR0805-FX-1002ELF/3593209) | 0.1 |
| 0805 resistor package (100K) | 2 | [Link](https://www.digikey.com/en/products/detail/bourns-inc/CR0805-FX-1003ELF/3740947) | 0.1 |
| 0805 resistor package (200K) | 1 | [Link](https://www.digikey.com/en/products/detail/bourns-inc/CR0805-FX-2003ELF/3784733) | 0.1 |
| 0805 capacitor package (0.1uF) | 4 | [Link](https://www.digikey.com/en/products/detail/nextgen-components/0805B104K500BD/15776052) | 0.078 |
| 0805 capacitor package (10uF) | 1 | [Link](https://www.digikey.com/en/products/detail/nextgen-components/0805W106K250CC/18676983) | 0.17 |
| 0805 capacitor package (4.7uF) | 2 | [Link](https://www.digikey.com/en/products/detail/nextgen-components/0805B475K160CC/22601960?s=N4IgjCBcpgLFoDGUBmBDANgZwKYBoQB7KAbXAAYAOAdlgCYQBdAgBwBcoQBlNgJwEsAdgHMQAXwJhqCEMkjps%2BIqRD06sMAFYmrDpG58hoiSDqaG0Waky4CxSGXV0AnGEo6Q7TjwEjxk50pnGTkFW2UHEHImEzpyWGDLUJslezJyADowAAIAVoAxEAJYDOo8wslyco8vfQBVQX42AHkUAFkcNCwAV14cfxAAWngk60U7FVcANnJpRhNB7VH5FInIiHmxMSA) | 0.34 |
| Analog divices Ideal Diodes MAX40200 | 2 | [Link](https://www.digikey.ie/en/products/detail/analog-devices-inc-maxim-integrated/MAX40200AUK-T/7599791) | 1.89 |
| Female SMA connector | 1 | [Link](https://www.digikey.ie/en/products/detail/molex/0732511153/11305709) | 3.9 |
| Lora Module | 1 | [Link](https://www.digikey.com/en/products/detail/rf-solutions/RF-LORA-868-SO/5291460) | 20.16 |
| Eggfinder (already have it) | 1 | — | — |
| Radio adapter Female connector. (already have it) | 1 | — | — |
| KB2040 MCU | 1 | [Link](https://www.adafruit.com/product/5302) | 8.95 |
|  |  |  |  |
| **Total SUM** |  |  | **61.808** |

**Total Estimated Component Cost: ~€62.00** (Excluding shipping/PCBs)

### Key Technical Revisions (Rev 1.2)

- **Ideal Diode Logic:** Swapped standard Schottky diodes for MAX40200 "Ideal" diodes to reclaim $500\text{mV}$ of battery headroom, ensuring stability deep into the discharge cycle.
- **RF Signal Integrity:** Implemented a $50\,\Omega$ coplanar waveguide ($0.1565\text{ mm}$ trace, $0.508\text{ mm}$ clearance) with via-fencing to maximize 868MHz range.
- **Expansion Logic:** Corrected the UART crossover (CBR_RX to RADIO_TX) to allow bi-directional communication with Eggtimer adapters.
- **Signal Cleanup:** Removed pull-up resistors on actively driven SPI lines (SCK/MOSI) to maintain sharp digital transitions at high clock speeds.

---
