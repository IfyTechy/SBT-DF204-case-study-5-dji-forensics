# DJI Mavic Air — Evidence Inventory

## 1. Android logical extraction

Evidence source: Android logical extraction archive.

Relevant artefacts:
- DJI flight TXT record dated 19 June 2018.
- FLY057.DAT flight telemetry.
- FLY058.DAT flight telemetry.
- Android cached MP4 video.
- DJI cached JPEG images.

## 2. EWF microSD forensic image

Evidence source: DF048.E01.

Format: Expert Witness Format (EWF).

Examination:
- Image integrity verification.
- FAT32 filesystem examination.
- DCIM directory listing.
- Extraction of five MP4 video files.
- Selected-frame visual examination.

## 3. Extracted microSD videos

- DJI_0001.MP4
- DJI_0002.MP4
- DJI_0003.MP4
- DJI_0004.MP4
- DJI_0005.MP4

## 4. Analysis outputs

- Sanitised FLY057 telemetry CSV.
- Sanitised FLY058 telemetry CSV.
- Sanitised telemetry analysis reports.
- Visual examination summary.
- CSV sanitisation and privacy verification records.

## 5. Evidence availability limitation

The raw microSD image was not successfully acquired during
this examination. The EWF image was acquired and independently
verified using the available forensic verification results.

The raw image's expected hash was supplied in the instructional
material and was not independently verified.

## 6. Preservation note

Original evidence files and complete forensic exports are
maintained separately in the private investigation workspace.

This public inventory describes the examined evidence sources
and publication outputs; it does not contain original evidence.
