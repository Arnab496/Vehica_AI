# VehicaAI Real-Time Event Dataset (Simulated)

## Provenance
This is a **realistic, event-driven synthetic dataset** for the VehicaAI prototype. It was not collected from actual vehicles, is not a live feed, and must not be presented as measured OEM data. Values are illustrative and intended for software development, RAG/QA demos, analytics, and dashboard prototyping.

## Coverage
- Time window: 2026-10-09T00:00:00+05:30 through 2026-10-22T23:59:00+05:30
- Sampling cadence: 1 minute per vehicle
- Vehicles: 3
- Telemetry rows: 60,480
- Unified event records: 12
- Trip summaries: 68
- Charging sessions: 35
- Timezone: Asia/Kolkata (+05:30)
- Random seed: 42
- Data origin marker: `synthetic_simulation`

## Files
- `vehicle_metadata.csv` — vehicle IDs and vehicle/pack metadata.
- `telemetry_1min.csv` — minute-level SOC, range, temperature, HVAC, power, tire pressure, ADAS and charging values.
- `vehicle_events_unified.csv` — searchable event timeline with severity, subsystem, code, context and next step.
- `diagnostic_events.csv` — diagnostic, battery-temperature and tire-pressure event subset.
- `adas_events.csv` — ADAS disengagement subset.
- `trip_summaries.csv` — trip duration, estimated distance, SOC delta, energy estimate and conditions.
- `charging_sessions.csv` — derived charge windows, SOC delta and estimated energy added.
- `hourly_environment.csv` — hourly ambient-condition aggregates derived from synthetic telemetry.
- `example_rag_queries.csv` — demo questions, retrieval hints and grounded answer outlines.
- `signal_dictionary.csv` — field definitions.
- `manifest.json` — dataset version, provenance and counts.

## Included demo scenarios
1. VEH-001: estimated range reduction correlated with high HVAC load, warm weather and stop-and-go traffic.
2. VEH-002: simulated battery temperature rise leading to a BMS warning at 2026-10-16 11:30 (+05:30).
3. ADAS disengagement examples: lane-marking loss, heavy rain, glare, construction-zone context.
4. VEH-003: front-right tire-pressure decline before a warning.
5. Diagnostic notice and inverter-cooling performance flag.
6. AC charging sessions and trip summaries.

## Recommended use
1. Ingest `telemetry_1min.csv` and `vehicle_events_unified.csv`.
2. Store records locally in SQLite with indexes on vehicle ID and timestamps.
3. Retrieve a time window (for example, 30 minutes before an alert).
4. Summarize evidence before asking a local LLM to explain it.
5. Include timestamps and observed readings in answers; avoid unsupported causal claims.
6. Verify offline functionality after all packages and models are installed.

## Limitations
Event codes are demo codes, not official manufacturer DTCs. Range and energy are estimates from simplified assumptions. No actual CAN bus, OEM telematics, live weather, cloud, or GPS integration is included. Warning thresholds are illustrative, not manufacturer service specifications.
