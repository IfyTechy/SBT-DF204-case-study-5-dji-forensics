# SBT-DF204: Case Study 5 - Investigating DJI Mavic Air Flight Evidence

[![Course Code](https://img.shields.io/badge/Course-SBT--DF204-blue.svg)](https://e-campus.unn.edu.ng)
[![Assessment](https://img.shields.io/badge/Assessment-Case%20Study%205-orange.svg)]()
[![Discipline](https://img.shields.io/badge/Discipline-Computer%20Forensics-purple.svg)]()

## Overview
This repository contains the documentation, evidence logs, UTC flight timeline, and reporting assets for **Case Study 5** of the **SBT-DF204 Computer Forensics** course. 

The investigation centers on an offline forensic examination of an Android logical extraction (associated with the `dji.go.v4` application) alongside two representations of DJI Mavic Air internal microSD media (a raw image and an Expert Witness Format [EWF] image). The primary goal is to establish a reliable account of aircraft activity, record verification, media cross-corroboration, and evidence-led timeline reconstruction.

---

## Repository Structure
```text
dji-mavic-air-digital-forensics/
│
├── README.md
│
├── evidence/
│   └── evidence_inventory.md
│
├── analysis/
│   ├── txt/
│   │   ├── decoded_flight_record.txt
│   │   └── flight_record_analysis.txt
│   │
│   ├── dat/
│   │   ├── FLY057_analysis.txt
│   │   └── FLY058_analysis.txt
│   │
│   └── video/
│       ├── cached_video_metadata.txt
│       └── visual_examination.txt
│
├── reports/
│   ├── preliminary_findings.md
│   ├── evidence_correlation.md
│   ├── forensic_timeline.csv
│   └── final_forensic_report.pdf
│
├── logs/
│   └── sanitised_hashes_and_verification.txt
│
└── scripts/
    └── analyse_flight.py
```

## Case Materials & Preservation Summary
In accordance with forensic integrity standards, all original evidence sources were preserved unchanged[cite: 13]. Working copies were utilized for parsing and analysis, with SHA-256 integrity checks logged prior to and following examination[cite: 13].
* **Android Logical Image (`dji.go.v4`):** Mobile extraction containing DJI GO 4 application data, main flight logs (`.txt`), detailed flight logs (`.dat`), cached video (`.mp4`), and cached pictures[cite: 13].
* **Raw Internal microSD Image:** Raw sector/partition representation of the drone's internal storage[cite: 13].
* **EWF Image (`.E01`):** Expert Witness Format container used for integrity verification and cross-source comparison against the raw image[cite: 13].

## Core Investigation Tasks & Methodology
1. **Evidence Preservation & Integrity:** Verification of SHA-256 hashes, read-only mount implementation, and working-copy isolation for mobile and disk images[cite: 13].
2. **DJI GO 4 Artefact Location:** Identification of application directory paths for TXT flight records, cached MP4 videos, DAT detailed flight logs, and cached thumbnails/pictures[cite: 13].
3. **Main Flight Record (`.txt`) Analysis:** Extraction of device/aircraft metadata, start/end conditions, location tracks, duration, and time-zone normalisation to UTC[cite: 13].
4. **Cached Video (`.mp4`) Validation:** Examination of source file paths, integrity hashes, metadata, duration, and synchronization scope relative to main flight records[cite: 13].
5. **Detailed Flight Record (`.dat`) Analysis:** Evaluation of power-on to power-off operational scopes to corroborate motor activation, take-off, flight routing, and landing events[cite: 13].
6. **Cached Pictures Inspection:** Documentation of capture sequences, file metadata, hashes, and strict technical limitations regarding inferences of operator identity or physical presence[cite: 13].
7. **Raw microSD & EWF Comparison:** Sector/partition analysis, media serial number/GUID validation, timestamp comparison, and binary/hash cross-corroboration between raw and EWF containers[cite: 13].
8. **UTC Timeline Reconstruction & Limitations:** Sequential mapping of physical events separated from direct observations vs. inferences, noting time-zone discrepancies, cache limits, and attribution caveats[cite: 13].
