# Roadmap

This roadmap is deliberately gated by evidence. Scaling the workspace is deferred until the EDM process and local precision loop are stable.

## M0 — Architecture freeze

- [x] Separate macro motion, fine motion, and gap servo conceptually.
- [x] Define EDM drilling as the first material-removal test.
- [ ] Select independent displacement measurement method for fine-stage validation.
- [ ] Select first electrode diameter range and workpiece coupon.
- [ ] Define the first dielectric/flushing arrangement.

Exit criterion: every Phase-1 subsystem has a measurable input/output and a failure criterion.

## M1 — Fine-Z metrology

- [ ] Build one printed flexure axis.
- [ ] Measure forward/reverse repeatability over at least 20 cycles.
- [ ] Measure 10 min and 60 min drift.
- [ ] Measure response to spindle vibration and fluid flow.
- [ ] Characterize screw pitch/nonlinearity separately from flexure hysteresis.

Exit criterion: demonstrate reproducible fine motion using an independent sensor. Target values are experimental; no micron-class claim is accepted from step-count calculations alone.

## M2 — Electrical state sensing

- [ ] Build isolated voltage/current acquisition front end.
- [ ] Implement waveform capture.
- [ ] Define state classifier: OPEN / DISCHARGE / ARC / SHORT.
- [ ] Test classifier against recorded waveforms before closing the motion loop.

Exit criterion: discharge-state classification is stable enough to drive a conservative retract/advance state machine.

## M3 — First controlled material removal

- [ ] Integrate fine Z + electrode + dielectric + energy-limited pulse source.
- [ ] Demonstrate automatic short recovery.
- [ ] Produce first repeatable micro-hole series.
- [ ] Measure entry diameter, depth, taper, and electrode wear.

Exit criterion: a repeated hole series can be produced without manual gap intervention.

## M4 — Process stability

- [ ] Compare stationary vs rotating electrode.
- [ ] Compare flushing strategies.
- [ ] Build debris/short-rate metrics.
- [ ] Establish tool-length reference procedure.
- [ ] Quantify tool-wear ratio and drift.

Exit criterion: identify a stable operating window and document uncertainty.

## M5 — Fine XY / milling

- [ ] Add tool-side fine XY flexure.
- [ ] Generate raster / contour toolpaths.
- [ ] Add wear compensation.
- [ ] Machine first controlled micro-slot/cavity.

Exit criterion: dimensional error is explainable by measured positioning, gap, and wear terms.

## M6 — Macro/micro hybridization

- [ ] Add coarse XY platform.
- [ ] Implement local fiducial registration.
- [ ] Implement tile overlap and stitching calibration.
- [ ] Demonstrate local micro-machining at multiple widely separated macro positions.

Exit criterion: local feature quality does not materially depend on absolute macro-stage positioning error within the fine-stage capture range.

## M7 — Large work envelope

Only after M6.

- [ ] Scale coarse travel.
- [ ] Add environmental/thermal compensation as needed.
- [ ] Evaluate large workpiece fixturing and fluid containment.
- [ ] Automate electrode handling / dressing if wear dominates throughput.
