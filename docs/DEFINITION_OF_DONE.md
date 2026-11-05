# Definition of Done

The project is complete when every required item below is checked and has the listed evidence. Leave an item unchecked until the evidence exists.

## Camera calibration

- [ ] Calibrate the camera using at least 20 calibration photos.
- [ ] Record the reprojection error in pixels and save the calibration output in `calibration/calibration_output.txt`.

## Dataset and evaluation

- [ ] Create and commit the fixed train, validation and test split before training begins. The split contains 56 training images, 16 validation images and 8 test images. Add the commit link here: `<commit link>`.
- [ ] Capture at least 70 original photos, undistort them and label them. Keep the images and CVAT annotation export under `dataset/`.
- [ ] Train the model and report its test-set IoU, mAP at 0.5 and 0.5:0.95, precision and recall in `measurement/test_metrics.json`.

## Measurement behavior and accuracy

- [ ] Run the measurement command on a new photo. It reports notebook width and height in millimetres when the image is usable.
- [ ] Check that the command clearly reports when the notebook or reference marker cannot be found. Save example outputs for both cases.
- [ ] Compare measurements against calliper values for at least 10 notebook instances. Report mean, median and worst absolute error in `measurement/accuracy_output.txt`.
- [ ] Include raw-image and undistorted-image errors side by side in `measurement/accuracy_output.txt`.
- [ ] Test camera tilt, document which images are refused and report how refusal affects the error of accepted readings. Save results in `measurement/sweep_output.txt`.

## Performance and release

- [ ] Measure inference time five times using the same machine and image. Record the results in `measurement/benchmark_output.txt`.
- [ ] Publish the trained weights and add the release link and SHA-256 hash to the README.

## Work left incomplete

List any unfinished items here. Write `None` if every item above is complete.

<unfinished items or None>
