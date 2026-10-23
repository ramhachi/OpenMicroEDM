# Safety

OpenMicroEDM is an experimental machine-tool project. EDM combines electrical energy, conductive liquid/debris, moving machinery, sharp micro-electrodes, and process-generated contamination.

## Electrical

- Keep the discharge power stage galvanically isolated from USB, PC, motion-control, and measurement interfaces unless a deliberate rated isolation path is used.
- Use hard current/energy limiting independent of firmware.
- Use fusing, an emergency disconnect, and enclosure interlocks.
- Keep energized conductors inaccessible during operation.
- Discharge stored energy before touching the pulse-power section.
- Do **not** use a mains-referenced improvised pulse circuit.
- Select probes/instruments with voltage/category ratings appropriate to the actual circuit.

## Fluid

- Contain splashes and leaks so dielectric fluid cannot reach non-protected electronics.
- Conductive debris changes dielectric behavior over time; monitor/maintain the fluid instead of assuming its initial conductivity remains constant.
- If hydrocarbon EDM oil is ever used, treat it as a fire and ventilation problem and use equipment/materials intended for it.
- For early benchtop work, deionized water is attractive from a handling standpoint and is used in micro-EDM literature, but it still requires contamination control, corrosion awareness, and electrical containment.

Background on dielectric roles and common use of deionized water in micro-EDM/wire EDM: <https://www.mdpi.com/2075-1702/11/9/906>

## Mechanical

- Enclose rotating electrodes and couplings.
- A very thin tungsten electrode is a needle-like projectile/sharp hazard when broken.
- Limit spindle energy during early experiments.
- Provide hard travel limits so a control fault cannot drive the electrode fixture into the work or bath hardware.

## Process

- Start with deliberately low stored/pulse energy and a small workpiece.
- Verify sensing and short-recovery behavior before unattended operation.
- Log abnormal sustained arcs and stop on repeated recovery failure.
- Keep a transparent separation between experimental settings and validated safe operating envelopes.

## Materials / waste

EDM debris contains fine particles from electrode and workpiece materials. Handle spent dielectric and filters according to the materials actually machined; do not assume metal-bearing waste is equivalent to clean water.
