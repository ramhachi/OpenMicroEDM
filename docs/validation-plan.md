# Validation Plan

## Philosophy

The project is only interesting if the low-cost architecture survives measurement. Every claim should be tied to an independent observation rather than inferred from motor steps or CAD dimensions.

## E000 — Fine-stage repeatability

Question: can the printed flexure stage return to commanded positions reproducibly?

Measure:
- forward and reverse approaches;
- at least 20 cycles per position;
- multiple positions across the useful stroke;
- ambient temperature;
- short-term and 60 min drift.

Report:
- mean error;
- standard deviation;
- peak-to-peak repeatability;
- hysteresis between approach directions;
- drift versus time/temperature.

Failure mode to look for: a stage that has excellent theoretical step resolution but poor physical repeatability.

## E001 — Disturbance sensitivity

Question: does electrode rotation or dielectric flow move the fine stage enough to matter?

Compare fine-stage output with:
- spindle off / on;
- representative spindle speed range;
- fluid off / on;
- combined spindle + fluid.

Use the same external displacement measurement as E000.

## E010 — Gap-signal acquisition

Question: can low-cost isolated sensing separate open gap, transient discharge, sustained arc, and hard short?

Record raw voltage/current waveforms under deliberately conservative pulse energy.

Do not close the servo loop until the state labels are understandable from recorded data.

## E011 — Short-recovery state machine

Question: can the Z axis automatically escape a short and re-enter a useful discharge state?

Metrics:
- recovery success rate;
- recovery time distribution;
- number of repeated short/recovery cycles;
- actuator travel used;
- false retractions during useful discharges.

## E020 — First hole series

Question: can the system drill repeated features without manual gap intervention?

Start with a 100–300 µm-class tungsten electrode and a conductive steel coupon. This is an engineering starting range, not a guaranteed resulting hole diameter.

For each hole log:
- command history;
- gap V/I data;
- machining duration;
- electrode length before/after;
- entry diameter;
- depth;
- taper if measurable;
- visible recast/edge damage.

## E021 — Electrode rotation

Question: does rotation improve stability enough to justify spindle complexity?

A/B comparison:
- same pulse condition;
- same electrode/workpiece;
- stationary vs rotating electrode;
- compare short frequency, machining time, dimensional consistency, and tool wear.

Literature motivation: debris transport and tool rotation materially affect the narrow inter-electrode region in micro-EDM. See <https://www.mdpi.com/2072-666X/17/6/747>.

## E022 — Flushing

Question: which low-cost fluid strategy gives stable debris removal without disturbing the fine stage?

Compare at minimum:
- static bath;
- gentle recirculation;
- directed flushing if mechanically feasible.

Treat fluid conductivity as a measured process variable rather than assuming fresh DI water remains unchanged during machining.

## E030 — Tool-wear compensation

Question: can electrode shortening be measured cheaply enough to support milling?

Candidate methods:
- periodic reference-pad touch-off;
- optical tool-length measurement;
- electrical contact/reference routine outside the machining region;
- model-based estimate corrected by periodic measurement.

## E040 — Local-coordinate stitching

Only after fine XY milling works.

Question: can a coarse stage reposition to a new tile and recover a local micron-scale coordinate frame?

Procedure:
- machine or mount fiducials;
- move macro stage away and back;
- measure apparent offset with camera/metrology;
- use fine XY to correct;
- repeat across widely separated macro positions.

Success is local registration within fine-stage capture range with quantified residual error. It is not proof of global macro-stage accuracy.
