# Aegion — System Architecture v0.1

## 1. System Overview

Aegion is divided into three primary electrical domains:

1. Field Power / I/O Domain
2. Isolated Communication Domain
3. Logic / Processing Domain

```text
                         AEGION
┌──────────────────────────────────────────────────────────┐
│                                                          │
│  24 V FIELD INPUT                                        │
│       │                                                  │
│       ▼                                                  │
│  ┌───────────────┐                                       │
│  │ Input         │                                       │
│  │ Protection    │                                       │
│  └───────┬───────┘                                       │
│          │                                               │
│          ├───────────────┐                               │
│          │               │                               │
│          ▼               ▼                               │
│     24 V FIELD      DC/DC POWER                         │
│     POWER RAIL      CONVERSION                           │
│          │               │                               │
│          │               ▼                               │
│          │        LOGIC POWER                            │
│          │               │                               │
│          │               ▼                               │
│          │        ┌────────────┐                         │
│          │        │  STM32G4   │                         │
│          │        │            │                         │
│          │        └─────┬──────┘                         │
│          │              │                                │
│          │       ┌──────┴──────┐                         │
│          │       │             │                         │
│          ▼       ▼             ▼                         │
│     24 V DI   Analog        Diagnostics                  │
│               Inputs                                     │
│                                                          │
│     24 V DO                                             │
│       ▲                                                  │
│       │                                                  │
│   Protected                                             │
│   High-Side                                             │
│   Drivers                                               │
│                                                          │
│                                                          │
│       STM32G4                                            │
│          │                                               │
│     ┌────┴────┐                                          │
│     │         │                                          │
│     ▼         ▼                                          │
│   CAN-FD    RS-485                                      │
│     │         │                                          │
│    ISO       ISO                                        │
│     │         │                                          │
│     ▼         ▼                                          │
│  FIELD CAN  FIELD RS-485                                │
│                                                          │
└──────────────────────────────────────────────────────────┘
