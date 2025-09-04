# 🧩 Problem Statement: Integrating FrSky FBUS Protocol into Custom Hardware

## Objective  
Enable reliable communication between FrSky FBUS-enabled receivers and custom actuator or telemetry hardware by decoding and implementing the proprietary FBUS protocol on a non-FrSky platform.

## Background  
FrSky’s FBUS protocol consolidates SBUS and S.Port telemetry into a single, high-speed serial stream (typically **100000 baud, 8N1, inverted logic**). While it offers streamlined wiring and reduced latency, FBUS remains undocumented and proprietary, posing significant challenges for developers seeking to integrate third-party hardware—such as custom servos, telemetry sensors, or flight control units—into FrSky ecosystems.
In current FrSky firmware, FBUS is functionally equivalent to F.Port2 — the terms are often used interchangeably in manuals and menus.

## Challenges  
- **Protocol Obfuscation**: FBUS lacks public documentation, requiring reverse engineering to identify packet structure, sync patterns, and telemetry mappings.  
- **Timing Sensitivity**: At 100000 baud, precise timing and interrupt handling are critical, especially on resource-constrained microcontrollers.  
- **Bidirectional Communication**: Unlike SBUS (unidirectional), FBUS supports telemetry return, requiring dynamic role switching and collision avoidance.  
- **Compatibility Mapping**: FBUS behavior varies across receiver models (e.g., Archer Plus vs. legacy RX), and may include undocumented quirks or channel remapping.

## Goal  
Develop a modular, reusable FBUS decoding and response stack that can be embedded into custom hardware platforms—enabling full actuator control and telemetry exchange with FrSky receivers, while maintaining diagnostic transparency and system reliability.

## Hardware
- Requires an inverted UART at 100000 baud (100k), 8N1.
- Some receivers benefit from a 4.7k–10k pull‑down resistor between signal and ground to stabilise the line, especially with long leads or noisy environments.
