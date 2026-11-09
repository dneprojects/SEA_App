# Smart Energy Agent

Energy-aware detection, monitoring and (later) tariff-/PV-optimized control for
Home Assistant. Current status: Phase 1 – monitoring and curation.

Concept (German): see [`EnergyAgent_Konzept.md`](EnergyAgent_Konzept.md).

## Usage (Phase 1)

The UI shows the detected entities grouped by energy role. Config/diagnostic
entities (LEDs, flags, setpoints, device battery levels) are hidden
automatically. Measurements (PV/grid/battery/power/energy) are included by
default, controllable candidates (switches/lights/climate) are not — enable
those with the checkbox. Use the role dropdown to fix a misclassification.
The selection is stored in `overrides.json` (next to the history DB, usually
`/data`) and survives restarts.

The "included only / all candidates" toggle reveals the not-yet-included
suggestions.

## Test environment without real PV/battery

If the test HA has no PV/storage system, the template sensors in
[`examples/ha_sim_sensors.yaml`](examples/ha_sim_sensors.yaml) simulate a
realistic daily profile (PV, house load, battery SoC/power, grid). See the file
header for how to include them.

## Run mode: Home Assistant App only

SEA runs only as a Home Assistant App (add-on, HA OS / Supervised) with a
license. Add the repository as an app repository and install via the
Supervisor. It uses Ingress (`config.yaml`, `Dockerfile`) and the
`SUPERVISOR_TOKEN` the Supervisor provides; without that token it does not
start. Publishing is automated, see [`DEPLOYMENT.md`](DEPLOYMENT.md).

## Configuration (environment variables)

| Variable | Default | Meaning |
|---|---|---|
| `SUPERVISOR_TOKEN` | – | provided by the Supervisor; required |
| `SEA_LOG_LEVEL` | `info` | debug/info/warning/error |
| `SEA_HISTORY_DB` | `/data/smart_energy_agent.db` | SQLite path (volume) |
| `SEA_HISTORY_DAYS` | `90` | raw history retention (days) |
