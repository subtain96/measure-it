# Project plan

## Measurement setup

Measure the width and height of one A5 notebook (about 210 x 148 mm). Use the same notebook throughout the project. Place it flat beside an ArUco reference marker on the same plane. Measure the marker's printed side with a calliper and record that value in `inference/settings.py`.

Use a Google Pixel 7 with focus, zoom and image resolution fixed for every photo. Keep the notebook and marker in focus and fully visible. The system should report width and height in millimetres only when the image and reference pass the reliability checks; otherwise it should explain why it cannot provide a reliable reading.

## Work plan (8 hours)

| Step | Hours | Evidence |
|---|---:|---|
| Finalize this plan, objectives and the fixed test split | 0.25 | Commit before training |
| Print calibration board and marker; capture at least 25 calibration photos and 80 notebook photos | 1.25 | Images and measured marker size |
| Calibrate the camera, undistort images and inspect straight edges | 0.5 | Calibration output and undistortion check |
| Label the notebook images in CVAT and export COCO annotations | 1.5 | Annotation export and fixed dataset split |
| Train Mask R-CNN and prepare the measurement command | 1.5 | Saved weights and command output |
| Compare measured dimensions with calliper measurements | 1 | Accuracy table with mean, median and worst error |
| Measure behavior at different camera tilts and set refusal thresholds | 1 | Sweep results and refusal counts |
| Complete documentation, record the weights hash and prepare the demo | 1 | README and demo |

## Scope

- Use Mask R-CNN ResNet50-FPN with COCO-pretrained weights.
- Use the ArUco marker in the notebook's plane as the scale reference.
- Limit augmentation to horizontal flips and brightness changes.
- Do not include multi-object scenes, a hyperparameter search or perspective correction in this version.

## Accuracy checks

- Compare both reported dimensions against calliper measurements on at least 10 notebook instances.
- Record signed error (system measurement minus calliper measurement) and absolute error in millimetres.
- Report mean, median and worst absolute error. Include raw-image and undistorted-image results when available.
- Test tilted photos separately. Record which photos are refused and how refusal changes the error among accepted readings.
- Keep the test split fixed before training and use it only for final evaluation.
