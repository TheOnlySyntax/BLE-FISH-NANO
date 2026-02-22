# BLEShark Nano — Pin Connections

> ⚠️ **Disclaimer:** This is a community-researched pinout. It is **not official** documentation from InfiShark. Information was gathered through reverse engineering and community investigation. Use at your own risk.

---

## Chip

**Seeed Studio XIAO ESP32-C3** (or compatible SuperMini ESP32-C3 wifi and ble functions wont work tho)

---

## Pin Map

| GPIO | Function | Notes |
|------|----------|-------|
| GPIO0 | LEFT button (secondary) | Boot strapping pin — activates as LEFT during boot |
| GPIO6 | OLED SDA | I2C Data |
| GPIO7 | OLED SCL | I2C Clock |
| GPIO8 | OK button | Primary select/confirm |
| GPIO9 | LEFT button (primary) | Navigate left/up |
| GPIO20 | RIGHT button | Navigate right/down |
| GPIO21 | IR TX | Infrared transmitter (TSAL6200 or similar) |
| GPIO10 | IR RX | Infrared receiver (TSOP4838 or similar)  |

---

## Display

| Spec | Value |
|------|-------|
| Size | 0.66 inch |
| Resolution | 64×48 px |
| Driver | SSD1306 |
| Interface | I2C |
| SDA | GPIO6 |
| SCL | GPIO7 |

> ⚠️ This is a **non-standard** resolution. Standard SSD1306 modules are 128×64 or 128×32. The 64×48 variant is specific to the XIAO ecosystem (available on AliExpress as "0.66 inch OLED 64x48 SSD1306").

---

## Buttons

| Button | GPIO | Notes |
|--------|------|-------|
| LEFT | GPIO9 | Primary |
| LEFT | GPIO0 | Secondary — boot pin side effect |
| RIGHT | GPIO20 | |
| OK / SELECT | GPIO8 | |

---

## Infrared

| Function | GPIO | Component |
|----------|------|-----------|
| IR TX | GPIO21 | TSAL6200 or similar IR LED |
| IR RX | GPIO10 | TSOP4838 or similar |

---

## PCB

> 🔧 **PCB schematic — incoming**
><img width="448" height="551" alt="image" src="https://github.com/user-attachments/assets/dbfffab0-0697-4dfb-a995-54f89a270bed" />
> A community-made PCB schematic is currently being worked on. It will include full hardware layout, component values, and a DIY build guide. Stay tuned.

---

## Notes

- GPIO0 acts as the LEFT button as a side effect of being the boot strapping pin. The firmware handles this gracefully after boot.
- InfiShark's firmware is **closed-source** but you can make it yourself so enjoy !.
---

## Contributing

If you have corrections, additional findings, or have traced more pins — PRs and issues are welcome!

---

*This document is community-maintained and not affiliated with InfiShark Technologies Inc.*
