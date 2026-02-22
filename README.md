# 🦈 BLEShark Nano — Pin Connections

> [!WARNING]
> **Disclaimer:** This is a community-researched pinout. It is **not official** documentation from InfiShark. Information was gathered through reverse engineering and community investigation. **Use at your own risk.**

---

## 📦 Chip

| | |
|---|---|
| **Official** | Seeed Studio XIAO ESP32-C3 |
| **Compatible** | SuperMini ESP32-C3 *(note: WiFi & BLE may not work on clones)* |

---

## 🗺️ Pin Map

| GPIO | Function | Notes |
|------|----------|-------|
| `GPIO0` | LEFT button *(secondary)* | Boot strapping pin — activates as LEFT during boot |
| `GPIO6` | OLED SDA | I2C Data |
| `GPIO7` | OLED SCL | I2C Clock |
| `GPIO8` | OK button | Primary select / confirm |
| `GPIO9` | LEFT button *(primary)* | Navigate left / up |
| `GPIO20` | RIGHT button | Navigate right / down |
| `GPIO21` | IR TX | Infrared transmitter — TSAL6200 |
| `GPIO10` | IR RX | Infrared receiver — TSOP4838 |
| `GPIO4` | Battery ADC | Voltage divider (2× 220kΩ) |

---

## 🖥️ Display

| Spec | Value |
|------|-------|
| Size | 0.66 inch |
| Resolution | **64×48 px** |
| Driver | SSD1306 |
| Interface | I2C |
| SDA | GPIO6 |
| SCL | GPIO7 |

> [!NOTE]
> This is a **non-standard** resolution. Common SSD1306 modules are 128×64 or 128×32. The 64×48 variant is specific to the XIAO ecosystem — search AliExpress for `0.66 inch OLED 64x48 SSD1306`.

---

## 🔘 Buttons

| Button | GPIO | Type | Notes |
|--------|------|------|-------|
| LEFT | `GPIO9` | Primary | 6×8mm tactile switch |
| LEFT | `GPIO0` | Secondary | Boot pin side effect |
| RIGHT | `GPIO20` | Primary | 6×8mm tactile switch |
| OK / SELECT | `GPIO8` | Primary | 6×8mm tactile switch |

All buttons are **active LOW** with internal pull-up.

---

## 🔦 Infrared

| Function | GPIO | Component | Notes |
|----------|------|-----------|-------|
| IR TX | `GPIO21` | TSAL6200 | Via MMBT3904Q NPN transistor driver |
| IR RX | `GPIO10` | TSOP4838 | 38kHz carrier frequency |

### IR TX Circuit

```
VCC (3.3V)
    │
 TSAL6200 (IR LED)
    │
  R1 27Ω
    │
  Collector ──┐
  Q1 MMBT3904 │  NPN transistor
  Emitter ────┴── GND
  Base
    │
  R2 270Ω
    │
 GPIO21
```

---

## 🔋 Battery

| Component | Value | Notes |
|-----------|-------|-------|
| R3 | 220kΩ | VCC → GPIO4 |
| R4 | 220kΩ | GPIO4 → GND |
| Switch | SS12D00G4 | Slide switch, 7.8×4mm cutout |
| Connector | JST 1.25mm | BAT+ / BAT- to XIAO pads |

Voltage divider formula: `VBAT × (220k / 440k) = VBAT / 2`
At full charge 4.2V → ADC reads **2.1V** ✅

---

## 🔧 PCB Schematic

> [!WARNING]
> PCB is **untested** — only attempt if you know what you're doing!

<img width="412" height="552" alt="BLEShark Nano PCB schematic page 1" src="https://github.com/user-attachments/assets/75fabd3a-624c-47ac-843d-a72382709402" />

<img width="448" height="551" alt="BLEShark Nano PCB schematic page 2" src="https://github.com/user-attachments/assets/dbfffab0-0697-4dfb-a995-54f89a270bed" />

---

## 📝 Notes

- `GPIO0` acts as a secondary LEFT button as a side effect of being the ESP32-C3 boot strapping pin. The firmware handles this gracefully after boot.
- InfiShark's firmware is **closed-source**, but the hardware is open enough to build your own — enjoy! 🛠️
- For open-source alternatives with similar functionality, check out [ESP32 Marauder](https://github.com/justcallmekoko/ESP32Marauder) or [Bruce Firmware](https://github.com/pr3y/Bruce).

---

## 🤝 Contributing

Found a mistake? Traced more pins? Have a better PCB layout?

**PRs and issues are welcome!** Every contribution helps the community.

---

<sub>This document is community-maintained and not affiliated with InfiShark Technologies Inc.</sub>
