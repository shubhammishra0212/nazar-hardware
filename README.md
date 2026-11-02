# nazar-hardware

Circuit, wiring and mechanical files for **NAZAR** — the AI washer-inspection conveyor built by Team Parakh at INDUX 5.0 (PS-04, Edge-AI multi-sensor quality inspection).

**Start here:** [`docs/NAZAR-00-Hardware-Bringup.pdf`](docs/NAZAR-00-Hardware-Bringup.pdf) — parts, power, pin map, how each sensor works, and the step-by-step bring-up order.

## What's in this repo

| Folder | Contents |
|---|---|
| `docs/` | Bring-up guide (Markdown source + PDF) |
| `diagrams/` | Wiring renders: complete rig and one per block (power/LEDs/belt, I²C sensors, IR, DS18B20, reject gate), plus a 7-page A3 PDF |
| `cirkit/` | [Cirkit Designer](https://app.cirkitdesigner.com) project files (`.ckt`) — File › Import › Import Local Cirkit File |
| `mechanical/stl/` | Printed parts: motor saddle, 18T/36T gear plate, servo tower, sort arm, tunnel brackets |

## Pin map (ESP32 DevKitC 38-pin)

| Signal | GPIO |
|---|---|
| I²C SDA / SCL (INA219 0x40, MPU-6050 0x68, BH1750 0x23) | 21 / 22 |
| FC-51 IR OUT | 18 |
| DS18B20 DQ (4.7 kΩ pull-up) | 4 |
| MG996R reject gate (via 330 Ω) | 13 |
| Belt relay IN (active LOW) | 26 |

Power: 24 V adapter → LM2596 #1 at 5.5 V (ESP32 5V pin, servo, relay, and the belt motor via S1 → INA219 → relay) and LM2596 #2 at 12 V (LED tunnel only).

## The other NAZAR repos

- [nazar](https://github.com/shubhammishra0212/nazar) — overview, architecture, interface contract
- [nazar-firmware](https://github.com/shubhammishra0212/nazar-firmware) — ESP32 firmware + per-sensor bring-up sketches
- [nazar-vision](https://github.com/shubhammishra0212/nazar-vision) — PatchCore washer inspection service
- [nazar-agent](https://github.com/shubhammishra0212/nazar-agent) — root-cause statistics + 8D reports with a local LLM
- [nazar-console](https://github.com/shubhammishra0212/nazar-console) — the operator Mac app
