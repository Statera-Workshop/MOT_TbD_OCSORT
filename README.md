# MOT_TbD_OCSORT

**OC-SORT** - online multi-object tracking by detection on KITTI-MOTS: 25 detectors + the detections of FairMOT.

- Paper: Cao et al., CVPR 2023; official code: `noahcao/OC_SORT`
- Principle: observation-centric re-update (ORU), momentum (OCM), recovery (OCR)
- **(best)**: the best of the 10 trackers on that detector; last column = that best HOTA.
- Implementation: `common/mot/trackers.py` (`ocsort`), re-implemented after the official code, official defaults
  (the class docstring lists every value and every `[Unified]` difference). Causality check: all OK.

### Results (OC-SORT, official defaults, KITTI-MOTS val)

| detector | HOTA | DetA | AssA | MOTA | IDF1 | IDSW | car | pedestrian | tracker ms | pipeline ms | best tracker on this detector |
|---|---|---|---|---|---|---|---|---|---|---|---|
| cascade_rcnn | 0.574 | 0.518 | 0.638 | 0.578 | 0.695 | 52 | 0.662 | 0.485 | 0.37 | 35.2 | 0.625 |
| libra_rcnn | 0.568 | 0.518 | 0.625 | 0.565 | 0.695 | 68 | 0.674 | 0.461 | 0.46 | 26.9 | 0.599 |
| faster_rcnn | 0.540 | 0.484 | 0.606 | 0.544 | 0.679 | 63 | 0.661 | 0.420 | 0.44 | 25.4 | 0.582 |
| dynamic_rcnn | 0.529 | 0.485 | 0.579 | 0.538 | 0.665 | 70 | 0.639 | 0.419 | 0.41 | 25.4 | 0.579 |
| atss | 0.472 | 0.414 | 0.542 | 0.463 | 0.590 | 41 | 0.598 | 0.346 | 0.34 | 22.0 | 0.527 |
| gfl | 0.454 | 0.370 | 0.558 | 0.410 | 0.550 | 33 | 0.590 | 0.317 | 0.31 | 21.1 | 0.522 |
| v6 | 0.445 | 0.376 | 0.531 | 0.434 | 0.564 | 41 | 0.603 | 0.288 | 0.33 | 6.9 | 0.509 |
| retinanet | 0.435 | 0.374 | 0.510 | 0.420 | 0.546 | 47 | 0.574 | 0.297 | 0.33 | 21.4 | 0.535 |
| tood | 0.427 | 0.344 | 0.537 | 0.375 | 0.514 | 34 | 0.584 | 0.270 | 0.32 | 25.1 | 0.506 |
| x | 0.417 | 0.344 | 0.512 | 0.394 | 0.530 | 40 | 0.590 | 0.245 | 0.33 | 5.8 | 0.478 |
| ppyoloe | 0.414 | 0.360 | 0.482 | 0.403 | 0.505 | 48 | 0.632 | 0.197 | 0.35 | 6.6 | 0.487 |
| fcos | 0.413 | 0.341 | 0.502 | 0.380 | 0.505 | 35 | 0.549 | 0.277 | 0.31 | 21.9 | 0.493 |
| rtmdet | 0.396 | 0.317 | 0.501 | 0.359 | 0.484 | 27 | 0.587 | 0.205 | 0.30 | 6.5 | 0.465 |
| v10 | 0.380 | 0.307 | 0.479 | 0.348 | 0.467 | 36 | 0.559 | 0.201 | 0.31 | 8.1 | 0.455 |
| x2 | 0.377 | 0.312 | 0.458 | 0.349 | 0.477 | 25 | 0.578 | 0.177 | 0.30 | 5.3 | 0.452 |
| v9 | 0.376 | 0.294 | 0.491 | 0.325 | 0.447 | 25 | 0.572 | 0.181 | 0.29 | 12.2 | 0.460 |
| v8 | 0.361 | 0.283 | 0.470 | 0.317 | 0.431 | 27 | 0.566 | 0.156 | 0.29 | 5.6 | 0.443 |
| v11 | 0.357 | 0.274 | 0.479 | 0.300 | 0.412 | 27 | 0.572 | 0.141 | 0.29 | 6.7 | 0.435 |
| v12 | 0.347 | 0.267 | 0.459 | 0.296 | 0.410 | 23 | 0.535 | 0.159 | 0.30 | 8.7 | 0.424 |
| deformable_detr | 0.323 | 0.268 | 0.391 | 0.306 | 0.436 | 45 | 0.433 | 0.213 | 0.31 | 68.6 | 0.482 |
| v13 | 0.322 | 0.249 | 0.453 | 0.281 | 0.370 | 27 | 0.551 | 0.093 | 0.29 | 10.9 | 0.372 |
| v26 | 0.301 | 0.248 | 0.375 | 0.286 | 0.370 | 24 | 0.549 | 0.054 | 0.29 | 9.1 | 0.390 |
| fairmot | 0.293 | 0.219 | 0.397 | 0.256 | 0.373 | 22 | 0.449 | 0.138 | 0.28 | 8.5 | 0.387 |
| centernet | 0.267 | 0.195 | 0.379 | 0.225 | 0.324 | 20 | 0.410 | 0.124 | 0.25 | 7.8 | 0.395 |
| v1 | 0.252 | 0.219 | 0.292 | 0.244 | 0.335 | 88 | 0.370 | 0.133 | 0.30 | 6.2 | 0.374 |
| ssd | 0.251 | 0.212 | 0.309 | 0.238 | 0.315 | 21 | 0.499 | 0.003 | 0.25 | 29.5 | 0.288 |

### Score-threshold sensitivity (OC-SORT, HOTA with one common threshold)

| detector | 0.3 | 0.4 | 0.5 | 0.6 | 0.7 |
|---|---|---|---|---|---|
| deformable_detr | 0.462 | 0.442 | 0.389 | 0.323 | 0.240 |
| faster_rcnn | 0.524 | 0.534 | 0.536 | 0.540 | 0.525 |
| fcos | 0.505 | 0.496 | 0.462 | 0.413 | 0.331 |
| libra_rcnn | 0.548 | 0.556 | 0.562 | 0.568 | 0.565 |
| ppyoloe | 0.480 | 0.468 | 0.453 | 0.414 | 0.371 |
| rtmdet | 0.482 | 0.473 | 0.445 | 0.396 | 0.322 |
| v10 | 0.461 | 0.445 | 0.420 | 0.380 | 0.324 |
| v11 | 0.431 | 0.407 | 0.385 | 0.357 | 0.319 |
| v12 | 0.451 | 0.427 | 0.403 | 0.347 | 0.257 |
| v13 | 0.377 | 0.358 | 0.339 | 0.322 | 0.283 |
| v26 | 0.403 | 0.380 | 0.349 | 0.301 | 0.254 |
| v6 | 0.512 | 0.493 | 0.475 | 0.445 | 0.401 |
| v8 | 0.438 | 0.423 | 0.396 | 0.361 | 0.315 |
| v9 | 0.452 | 0.434 | 0.409 | 0.376 | 0.325 |
| x | 0.454 | 0.451 | 0.437 | 0.417 | 0.373 |
| x2 | 0.446 | 0.446 | 0.417 | 0.377 | 0.320 |

Part of the *Physical AI MOT* comparison of the **Statera Working Group**: 10 trackers x 25 detectors (+ the detections of FairMOT), 3 joint
detection-and-tracking networks and 1 end-to-end tracker under one protocol. The full comparison (Pareto front,
tracker ranking, JDT / E2E against tracking-by-detection) is in `MOT_Detectors_KITTIMOTS` (`RESULTS.md`).

## Protocol (all MOT_* repositories)

- Online / causal only: every method sees the current frame and its own state; checked by re-running prefixes of
  every sequence (the output of frame t must not change when later frames are removed).
- Input 1216 x 384 (KITTI 1242 x 375 letterboxed), detectors trained from scratch on KITTI-MOTS train (12 sequences),
  30 epochs, Adam 1e-4, effective batch 8, seed 777 - the protocol of the *Physical AI Object Detection* series.
- Metrics: HOTA / DetA / AssA (TrackEval classes, car / pedestrian mean), MOTA, IDF1, IDSW.
- Latency: RTX 4070 Laptop GPU, batch 1, fp32, medians over val; pipeline = detector (forward + post-processing) +
  ReID (appearance trackers) + tracker (CPU); image decoding / letterboxing not included.
- Trackers run with their official default parameters; frame-based values given for 30 fps are scaled to 10 fps.
  A sensitivity table with one common score threshold for every tracker is reported separately (chosen on val, so it
  is analysis, not ranking).

## Data: KITTI-MOTS (box level, val = 9 sequences, 2,981 frames)

KITTI tracking images (21 training sequences) with instance / track annotations; boxes = tight boxes of the masks,
classes car and pedestrian, ignore regions (id 10000) neither rewarded nor penalised. The annotations are taken from
the **KITTI-STEP** panoptic maps (same sequences and split, car / person instances merged from KITTI-MOTS; frames,
track counts and pedestrian masks match the KITTI-MOTS paper, car masks differ by 39 of 26,899).

```bash
bash tools/mot/get_kitti_mots.sh            # KITTI tracking images + annotations (KITTI-STEP fallback)
python tools/mot/kittimots_to_voc.py        # VOC-layout copy with tracks + count report
UNIFIED_IMAGE_DATASET=kittimots python tools/mot/count_loader.py     # counts as the loaders read them
```

**Licence of the data and of every trained weight here: KITTI / KITTI-MOTS / KITTI-STEP are CC BY-NC-SA 3.0
(non-commercial).**

## Usage

```bash
pip install -r requirements.txt
pip install "git+https://github.com/JonathonLuiten/TrackEval.git@12c8791b303e0a0b50f753af204249e622d0281a"
# saved detections (+ ReID features) of the 25 detectors: Release of Statera-Workshop/MOT_Detectors_KITTIMOTS
python tools/mot/run_tracker.py --source kittimots --dets dets/x_reid.npz --trackers ocsort --causal
python tools/mot/run_tracker.py --source kittimots --dets dets/x_reid.npz --gt-as-pred      # evaluation self-test
python tools/mot/mot_table.py                                                             # tables of all runs
```

`run_tracker.py --trackers` accepts every tracker of the comparison (iou, sort, bytetrack, ocsort, hybridsort, botsort, botsort_reid, deepsort, tracktrack, fairmot), so other
trackers can be run on the same detections. Results of this repository: `results/` (JSON per detector).

## Files

```
common/mot/trackers.py    the trackers of the comparison (default here: ocsort)
common/mot/core.py        boxes, IoU, assignment, Kalman filters, camera-motion estimation
common/mot/evaluate.py    KITTI-MOTS ground truth and TrackEval metrics
tools/mot/run_tracker.py  run / time / evaluate trackers on saved detections (+ causality check)
tools/mot/*kitti*         data preparation
results/                  evaluation JSON of this repository's tracker(s)
THIRD_PARTY.md            sources and licences
```

## Global Collaboration

Hills Robotics is currently participating in multiple projects in Korea and internationally.

We are actively interested in building relationships with organizations that can complement our technology with global sales networks, distribution channels, system integration capabilities, manufacturing ecosystems, AI infrastructure, robotics technologies, research capabilities, or strategic investment.

Several technology and business collaborations are already underway. Some partners, projects, system architectures, and commercial programs cannot be publicly disclosed because they are subject to confidentiality and business agreements.

We believe that the emerging Physical AI ecosystem cannot be built by a single company.
It requires a global network connecting robotics companies, AI researchers, semiconductor and computing companies, sensor manufacturers, software developers, universities, system integrators, industrial customers, investors, and global distribution partners.

We have now begun our serious exploration of the Physical AI frontier, and we welcome connections with people and organizations who want to build this ecosystem together.

## Research, Contribution, and Donation

The repositories of the Statera Working Group are intended to contribute to the broader technical discussion around Physical AI.

Researchers, engineers, developers, companies, universities, and independent contributors interested in these subjects are welcome to connect with us.

If you would like to collaborate on Physical AI or autonomous robotics, participate in research or technology development, discuss international business cooperation, propose technology or platform integration, contribute technical knowledge, or support this GitHub knowledge initiative through sponsorship or donation, please contact us.

## Contact

**Richard Minsoo Go**
Head of AI, Hills Robotics
Statera Working Group

Personal / Research Contact:
[gominsoo888@gmail.com](mailto:gominsoo888@gmail.com)

Hills Robotics / Business Contact:
[minsoo.go@hillslogis.com](mailto:minsoo.go@hillslogis.com)

Hills Robotics:
https://hillslogis.com/

For inquiries regarding next-generation outdoor autonomous robotic platforms, Physical AI Spider Grid, Intelligence Cabinet, Edge AI, or On-Premise AI architectures that are not yet publicly presented on the company website, please contact us directly.
