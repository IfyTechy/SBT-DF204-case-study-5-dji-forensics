# Sanitised DJI Flight Telemetry Datasets

## Overview
This directory contains publication copies of two DJI Mavic Air
flight telemetry datasets converted from DAT files using DatCon 4.3.0.

The original CSV exports are preserved separately in:
output/dat_analysis/

## Dataset inventory

| Dataset | Original columns | Published columns |
|---|---:|---:|
| FLY057 | 298 | 283 |
| FLY058 | 294 | 279 |

## Sanitisation

The following fields were excluded from the publication copies:

- GPS latitude and longitude
- IMU latitude and longitude
- Calculated latitude and longitude
- BatteryInfo:BatAuth:D
- Controller:D2H_x:D
- Controller:D2H_y:D
- VIO:posX
- VIO:posY

These exclusions reduce exposure of precise location and
potentially sensitive authentication or positional information.

Additionally, one aircraft serial identifier found in the
FLY058 `Attribute|Value` field was replaced with `[REDACTED]`.
The affected row and all dataset columns were preserved.

## Retained information

The datasets retain selected telemetry fields, including:

- Flight timestamps
- Flight controller modes
- Motor states and motor speeds
- Relative and absolute altitude measurements
- Velocity measurements
- GPS quality and satellite-count information
- Battery measurements

## Important limitations

These files are sanitised derivatives, not original forensic evidence.

Removing fields may limit some forms of flight reconstruction.
The original evidence and complete analysis exports remain preserved
in the private investigation workspace.

The published datasets should not be treated as substitutes for
the original DAT files or complete forensic records.
