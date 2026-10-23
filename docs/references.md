# References and design rationale

This is a living engineering bibliography. Links are included so design assumptions can be audited later.

## Precision flexure / upstream project

### RepRapMicron / PIKA

- Repository: <https://github.com/VikOlliver/RepRapMicron>
- Project page: <https://reprap.org/wiki/RepRapMicron>

Why it matters: demonstrates a low-cost FDM-printed flexure approach intended for repeatable micron-scale positioning over a small range, using familiar RepRap/CNC hardware. OpenMicroEDM borrows the architectural idea of low-cost flexure fine motion; it does not assume PIKA's complete mechanism can be copied unchanged into a tool-side EDM head.

### Flexure micro-positioning literature example (2026)

- <https://www.sciencedirect.com/science/article/pii/S2213846326000799>

Why it matters: modern precision stages continue to use flexure hinges specifically to avoid mechanical backlash and obtain controlled compliant motion. This does not validate PLA flexures by itself; it validates the general mechanism class.

## Micro-EDM process

### 2026 review: modelling, pulse generation, tool wear, debris, monitoring

- <https://link.springer.com/article/10.1007/s00170-026-18398-7>

Why it matters: current overview of micro-EDM physics and practical limitations. It describes micro-EDM as non-contact machining for conductive materials, discusses small inter-electrode gaps, RC/switch pulse generation, tool wear, debris, flushing, and monitoring. It is the primary background source for the architecture's risk list.

### 2026 dielectric/debris CFD study

- <https://www.mdpi.com/2072-666X/17/6/747>

Why it matters: directly studies dielectric flow, inter-electrode gap size, tool rotational speed, and debris-transport implications in micro-EDM milling. Supports treating spindle rotation/flushing as first-class experimental variables.

### EDM electrodes and dielectric fluids review

- <https://www.mdpi.com/2075-1702/11/9/906>

Why it matters: overview of electrode manufacture and dielectric-fluid functions. Notes the role of dielectric in insulation, cooling, and debris removal and discusses deionized water use in micro-EDM/wire EDM.

### Micro-EDM with RC pulse generator and tungsten electrode

- <https://link.springer.com/article/10.1007/s41871-025-00288-3>

Why it matters: practical recent example using an RC-type pulse generator and tungsten electrode, and explicitly studying tool-shape wear in micro-EDM drilling/milling. Supports prioritizing tool wear from the first experiments rather than adding compensation late.

### Process monitoring / waveform-based condition assessment

- <https://www.sciencedirect.com/science/article/pii/S2212827125006985>

Why it matters: highlights the narrow, stochastic inter-electrode gap and the need for process monitoring to maintain stable high-precision EDM. Supports logging voltage/current waveforms and building a gap-state estimator before aggressive servo tuning.

### Alternative fast gap-control concept

- <https://www.sciencedirect.com/science/article/pii/S0888327024010902>

Why it matters: example of a nontraditional gap-control mechanism (maglev) for micro-EDM. It is useful mainly as evidence that gap-servo dynamics are an active design problem rather than a fixed commodity solution.

## Interpretation rule

Literature values are **not** copied into the project as guaranteed machine specifications. They are used to:

1. identify plausible orders of magnitude;
2. identify failure modes;
3. choose experiments;
4. compare the prototype against prior art.

All OpenMicroEDM performance claims must come from this repository's own measured data with stated uncertainty and test conditions.
