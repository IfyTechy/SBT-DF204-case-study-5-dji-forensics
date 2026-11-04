# DIGITAL FORENSIC INVESTIGATION REPORT
## DJI Mavic Air - Case Study 5

**Investigation:** DJI Mavic Air Digital Forensic Examination  
**Case Reference:** DF048 / SBT-DF204 Case Study 5  
**Examiner:** Nebeuwa Ifeanyichukwu Raphael  
**Environment:** Kali Linux  

---

## 1. Executive Summary

This investigation examined digital artefacts associated with a
DJI Mavic Air drone. The examination focused on an Android logical
extraction and an Expert Witness Format (EWF) microSD forensic image.

The objectives were to examine available flight records, analyse
flight telemetry, verify evidence integrity, extract and examine
video files, and correlate relevant findings across evidence sources.

The Android extraction contained a DJI flight TXT record, two DAT
flight records, cached video and cached JPEG images.

The EWF image was successfully verified and examined. Five MP4
videos were identified and extracted from its FAT32 filesystem.

The raw microSD image was not successfully acquired. Consequently,
a direct comparison between the raw image and EWF image could not
be performed.

## 2. Investigation Objectives

The examination aimed to:

- Identify relevant DJI Mavic Air digital artefacts.
- Preserve and document available evidence.
- Calculate and verify cryptographic hashes.
- Decode and analyse flight telemetry.
- Examine the EWF microSD filesystem.
- Extract and examine available video files.
- Compare relevant timestamps and observations.
- Document findings, limitations and conclusions.

## 3. Evidence Sources

### 3.1 Android Logical Extraction

The Android logical extraction archive contained:

- DJI flight TXT record.
- FLY057.DAT.
- FLY058.DAT.
- Cached MP4 video.
- Cached JPEG images.

The archive was validated using ZIP integrity testing.
Its SHA-256 hash was recorded as:

`9a352b282d832556eb7cb73010ea281f9946d889438ce07d9bbee3b64229285`

### 3.2 EWF microSD Image

Evidence file: `DF048.E01`

The supplied EWF image was downloaded, integrity-verified and examined using forensic tools.

Its SHA-256 hash was recorded as:

`435b97c0cba3007d40b4ac10686049d1527fa0dc1235d8492a2df3e66d8bdac9`

Its MD5 hash was:

`d1651cfacd5b1827e337ad0a826002ae`

The MD5 matched the reference value supplied in the instructional
material.

EWF verification successfully confirmed the embedded media hashes:

- MD5: `7285a252d6c4582e120e06f3c13861ff`
- SHA-1: `8bb139ec8196e238d17e729ce9cfe585adfc616e`

### 3.3 Raw microSD Image

The raw microSD image was not successfully downloaded.

The expected MD5 value supplied in the instructional material was:

`08cf90ed4d61e232959b568a8fe5aee6`

This value was not independently verified. No conclusion about
the raw image's identity or equivalence to the EWF image is made.

## 4. Tools and Methodology

The examination used:

- Kali Linux.
- Python 3 and pandas.
- DatCon 4.3.0.
- djiparsetxt.
- Sleuth Kit utilities.
- libewf utilities.
- FFmpeg and ffprobe.
- ExifTool.
- SHA-256 and MD5 hashing utilities.

The methodology included evidence receipt and preservation, archive validation,
hash calculation, forensic image verification, filesystem examination,
file extraction, telemetry conversion, metadata examination and
selected-frame visual analysis.

Original evidence and complete analysis exports were preserved
separately from publication copies.

## 5. Android Flight Record Examination

The DJI TXT flight record was decoded using djiparsetxt.

A total of 3,055 decoded records were identified.

The decoded record timestamps extended from:

**2018-06-19 18:50:34.869**  
to  
**2018-06-19 18:55:40.243**

The calculated interval was approximately 5 minutes and 5 seconds.

The record included GPS_Atti, AutoTakeoff, AutoLanding and
EngineStart controller states.

The TXT record and FLY057 DAT telemetry show closely aligned
starting timestamps.

The decoder produced warnings concerning unhandled record types.
Therefore, the decoded output may not represent every available
record in the original TXT file.

## 6. DAT Flight Telemetry Examination

The two DAT files were converted to CSV using DatCon 4.3.0.

### 6.1 FLY057

- Records: 5,261.
- First GPS timestamp: 18:50:34 UTC.
- Last GPS timestamp: 18:55:39 UTC.
- Dominant flight mode: GPS_Atti.
- Other recorded modes included AutoTakeoff and AutoLanding.

The FLY057 timestamp range closely corresponds with the decoded
TXT flight record.

### 6.2 FLY058

- Records: 3,785.
- First GPS timestamp: 19:00:23 UTC.
- Last GPS timestamp: 19:02:08 UTC.
- Recorded modes were predominantly GPS_Atti, with some Atti entries.
- Controller motor-state values were zero in all 3,780 populated
  records examined.
- Four motor-speed fields were zero in all 3,775 populated records
  examined.

These observations are consistent with a stationary or ground-level
recording. They do not independently prove the aircraft's physical
state.

## 7. EWF Filesystem Examination

The EWF image was mounted for examination using ewfmount.

Filesystem analysis identified a FAT32 filesystem with an Android
OEM identifier.

The root directory contained folders including:

- DCIM
- LOST.DIR
- MISC
- System Volume Information
- .fseventsd

Five MP4 files were identified in the DCIM/100MEDIA directory:

- DJI_0001.MP4
- DJI_0002.MP4
- DJI_0003.MP4
- DJI_0004.MP4
- DJI_0005.MP4

The five videos were extracted using forensic filesystem
extraction methods. Their SHA-256 hashes were recorded and
successfully checked against the extracted files.

## 8. Video and Image Examination

Selected frames were extracted from the EWF videos and Android
cached video for visual examination.

The EWF footage included indoor technical-looking environments
and aerial views of dry open landscapes.

The sampled DJI_0002 footage showed at least two people.
Their identities and roles could not be established.

The Android cached video showed open grassland, a white tent,
people, vehicles and distant hills.

The cached JPEG images included indoor workshop-like scenes and
an outdoor landscape. No individual identities or exact locations
were established.

These observations are limited to the sampled frames and do not
represent complete video examinations.

## 9. Cross-Source Correlation

The Android TXT record and FLY057 DAT telemetry have closely
aligned starting timestamps and overlapping examination periods.

The Android cached video has a duration of approximately
240.97 seconds, while the decoded TXT record spans approximately
305.37 seconds.

The difference in duration means the cached video should not be
assumed to represent the complete flight.

The Android video filename contains 14:50:39, while the TXT
record and FLY057 telemetry begin at approximately 18:50 UTC.
The possible timezone explanation remains unverified.

The Android cached video and EWF videos DJI_0003, DJI_0004 and
DJI_0005 share broad landscape characteristics. However, visual
similarity does not establish that they are copies, segments or
recordings from the same flight.

No byte-for-byte matches were identified between the Android
cached video and the five extracted EWF videos.

## 10. Data Sanitisation for Public Release

Publication copies of FLY057 and FLY058 were prepared separately.

Fifteen potentially sensitive or positional columns were excluded
from each dataset.

One aircraft serial identifier in the FLY058 Attribute|Value
field was replaced with `[REDACTED]`.

The affected row and all dataset columns were preserved.

The published copies underwent checks for the specified location
column names and known aircraft and battery serial identifiers.

Both datasets passed these checks.

These checks do not constitute a guarantee that every possible
identifying value has been removed.

## 11. Limitations

The investigation has the following limitations:

1. The raw microSD image was unavailable for independent acquisition
   and comparison.
2. The expected raw-image hash was supplied by instructional
   material and was not independently verified.
3. The TXT decoder reported unhandled record types.
4. Video examination was based on selected frames rather than
   every frame.
5. Exact geographical locations and individual identities were
   not established.
6. The Android cached video duration differs from the TXT record
   duration.
7. The filename timezone interpretation remains unverified.
8. Visual similarities between recordings do not independently
   establish a common flight or mission.

## 12. Conclusion

The investigation successfully examined the available Android
logical extraction and EWF microSD image.

The Android extraction provided a decoded flight TXT record,
two DAT telemetry files, cached video and cached JPEG images.

The EWF image passed verification and contained five MP4 videos
that were extracted and examined.

The TXT record and FLY057 telemetry show closely aligned
timestamps. FLY058 contains telemetry observations consistent
with a stationary or ground-level recording, although this
interpretation is not conclusive.

Visual examination identified indoor technical-looking scenes
and aerial landscape footage. The available evidence did not
establish exact locations, individual identities or a definitive
relationship between the Android cached video and the EWF videos.

The unavailable raw microSD image remains an important limitation.
Further examination and comparison may be possible if that image
becomes available.

## 13. Final Assessment

The examination produced documented evidence-handling records,
integrity verification results, telemetry analysis, filesystem
findings, extracted media and sanitised publication datasets.

The conclusions in this report are limited to the evidence
successfully acquired and examined. Unverified interpretations
have been identified as such.

---

**End of Report**
