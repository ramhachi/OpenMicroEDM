# Firmware

Initial real-time responsibilities:

- sample/receive gap-state measurements;
- classify or consume OPEN / DISCHARGE / ARC / SHORT state;
- execute conservative fine-Z advance/hold/retract logic;
- enforce travel and fault limits independent of host software;
- timestamp actuator/state data for experiment logs.

The first controller should be understandable and auditable. Start with an explicit state machine before trying adaptive/ML control.
