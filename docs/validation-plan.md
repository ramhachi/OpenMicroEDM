# Validation Plan

## Philosophy

The project is only interesting if the low-cost architecture survives measurement. Every claim should be tied to an independent observation rather than inferred from motor steps, pixel size, or CAD dimensions.

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

## E005 — Static vision repeatability

Question: what is the noise floor of the camera + optics + illumination + localization algorithm without any machine motion?

Procedure:
- acquire at least 100 images of the same fiducial;
- keep motion stages fixed;
- log camera settings and temperature;
- estimate XY and rotation for every frame.

Report:
- apparent XY standard deviation and peak-to-peak variation in µm;
- rotation variation;
- dependence on exposure / illumination / focus;
- outlier rate and failure-detection behavior.

This experiment establishes the optical-metrology floor before stage errors are introduced.

## E006 — Vision scale / fine-stage calibration

Question: can image-estimated motion reproduce independently measured fine-stage displacement?

Procedure:
- apply calibrated small XY motions across the fine-stage workspace;
- image the same reference after each move;
- compare image-estimated displacement with independent displacement measurement where available;
- approach points from multiple directions.

Measure:
- pixel scale;
- distortion residual;
- XY orthogonality;
- cross-axis coupling;
- subpixel estimator bias;
- hysteresis;
- field-position dependence.

## E007 — Macro leave-and-return local registration

Question: can the machine abandon global absolute accuracy and recover the local frame optically?

Procedure:
1. establish a reference image / local frame;
2. move the macro stage away by a large randomized displacement;
3. return using only coarse motion;
4. reacquire the local fiducial or intrinsic feature;
5. estimate XY-theta residual with vision;
6. correct using fine XY;
7. acquire a verification image;
8. repeat at least 100 times with randomized approach directions.

Primary outputs:
- pre-correction coarse landing error;
- fine-stage correction magnitude;
- post-correction residual distribution;
- RMS / 95th-percentile / worst-case error;
- residual versus temperature, time, and approach direction.

Initial research target: final local XY residual on the order of 1 µm. This is a validation target, not a current claim.

## E008 — Tool-to-fiducial registration

Question: does the optical residual remain small when referenced to the actual electrode tool-center point rather than the image center?

Preferred method: observe electrode tip and fiducial in the same optical frame.

Fallback: use a calibrated camera-to-tool transform and verify it periodically.

Measure:
- camera-to-tool offset repeatability;
- drift after spindle operation / thermal cycling;
- sensitivity to tool replacement / electrode wear;
- final tool-to-fiducial residual.

This is the machining-relevant vision gate.

## E009 — Tile-to-tile stitching

Question: can overlapping local workspaces be registered without unacceptable accumulated error?

Procedure:
- define adjacent tiles with shared fiducials or intrinsic features;
- estimate the transform between each pair;
- propagate across multiple tiles;
- independently measure closure error where possible.

Report both local pairwise residual and accumulated global drift.

See [`vision-registration.md`](vision-registration.md) for the metrology architecture.

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

## E040 — Integrated local-coordinate machining

Only after fine XY milling and E005–E009 work.

Question: can a coarse stage reposition to a new tile, recover a local micron-scale coordinate frame, correct with fine XY, and machine a feature whose placement error is consistent with the measured registration uncertainty?

Success is local registration and machining within a quantified tool-relevant error budget. It is not proof of global macro-stage accuracy.
