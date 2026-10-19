# ACD Angle Capture

A mobile-friendly web app for capturing eye photographs at a **known, repeatable camera angle** (0° to 180°) relative to the visual axis. It was built for research on **anterior chamber depth (ACD)** analysis, where inconsistent camera angles between photos cause inconsistent ACD measurements.

> **Research use only.** This is not a medical device and must not be used for diagnosis or clinical decisions.

## The problem it solves

Photographing the eye from the temporal side "at 90°" by hand is not repeatable. Small changes in camera angle change the measured ACD. This app reads the phone's motion sensors, shows the live angle, and captures the image only when the phone is at your chosen target angle.

## Features

- Live camera angle from 0° to 180° with a dial display
- Target angle of your choice (quick buttons for 40°, 60°, 90°, 120°, or any value)
- Selectable tolerance (±0.5°, ±1°, ±2°, ±3°) and hold time
- Level (tilt) check so the phone is not pitched up or down
- Auto-capture when on target, or manual capture
- Full-resolution JPEG saved with the angle in the filename
- CSV log of every capture (subject ID, eye, target, measured angle, tilt, timestamp)
- **Captures are stored on the device** (browser storage) and are still there after closing or reloading the page
- **Share all to mentor**: sends every image plus the CSV through the phone's share sheet (WhatsApp, Gmail, Drive and so on)
- **Download ZIP** of all images and the CSV for emailing or archiving
- **Email summary** that opens an email to your mentor with the results table (files are sent separately)
- Delete single captures or clear all (with a confirmation tap)
- Works on Android and iPhone in the browser, with no installation
- Backup mode that uses the phone's own camera app if live camera access is blocked
- Light and dark mode

## How to use

1. Open the hosted link in **Chrome (Android)** or **Safari (iPhone)**.
2. Tap **Start camera and sensors** and allow camera and motion access.
3. Enter the subject ID and choose the eye (OD or OS).
4. Stand directly in front of the eye with the phone aimed at it and tap **Set 0° reference**. This defines the visual axis as 0°.
5. Set the target angle.
6. Move the phone around the eye, keeping it level and aimed at the eye, until the status shows **On target**.
7. The photo is captured automatically (or tap **Capture now**) and stored in the list.
8. To send your work, tap **Share all to mentor** (or **Download ZIP** and attach it to an email).

Redo step 4 for every subject.

### Output example

Filename: `P001_OD_target90_actual90.3_001.jpg`

| n | subject_id | eye | target_deg | measured_deg | tolerance_deg | tilt_deg | on_target |
|---|------------|-----|-----------:|-------------:|--------------:|---------:|-----------|
| 1 | P001 | OD | 90 | 90.3 | 1 | 0.8 | true |

The image is the raw camera frame with nothing drawn on it, so it can be measured in ImageMeter or any other tool.

## Hosting (GitHub Pages)

1. Upload all files in this repository to a GitHub repository.
2. Go to **Settings > Pages**.
3. Under **Build and deployment**, set the source to **Deploy from a branch**, choose the `main` branch and the `/ (root)` folder, then save.
4. After a minute or two your app is available at `https://<username>.github.io/<repository>/`.

The camera and motion sensors only work on an `https://` address, so opening `index.html` directly from the phone's storage will not work.

## Limitations

- The angle is estimated from the phone's gyroscope and compass sensors, so it depends on sensor quality and can drift. **Validate it against a protractor or printed angle template** before collecting study data, and report that validation in your methods.
- Magnetic interference (metal furniture, equipment) can affect readings on some phones.
- Captures are stored in the browser on that phone only. Clearing the browser's site data, using private browsing, or switching phones removes or hides them, so **share or download a ZIP backup regularly**.
- "Share all" depends on the phone's browser supporting file sharing. If it does not, use **Download ZIP**.
- In backup mode (phone camera app) the live angle is not visible during the shot. The recorded angle is the one read when you return to the page.
- iPhone requires you to grant Motion and Orientation access each session.

## Troubleshooting

| Problem | What to try |
|---|---|
| "Camera unavailable: permission denied" | Open the page in the phone's main browser (not inside another app), allow camera in the browser's site settings, and make sure the address starts with `https://`. |
| Angle shows `--` | Tap **Set 0° reference**. On iPhone, allow Motion and Orientation access. |
| No sensor data | The phone may lack a gyroscope, or the browser blocks it. A simulated slider appears for testing only. |
| Angle jumps or drifts | Move away from metal objects, keep the phone level, and redo the 0° reference. |

## Privacy

Everything runs in the browser on your device. The app does not upload images or data anywhere. Files leave your phone only when you choose to share or download them. If images show identifiable people, follow your ethics approval and consent requirements when sending them.

## Project files

- `index.html` – the complete app (HTML, CSS and JavaScript in one file)
- `README.md` – this file
- `LICENSE` – MIT license
- `CITATION.cff` – citation information
- `.gitignore` – files Git should ignore

## Citation

If you use this tool in published research, please cite it using the details in `CITATION.cff` (GitHub shows a "Cite this repository" button).

## License

Released under the [MIT License](LICENSE).
