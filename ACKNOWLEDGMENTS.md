# Acknowledgments & third-party licenses

rewindDV is developed by Rewind Digital. It builds on substantial open-source
engineering, and we are grateful to the people and organizations below.
This is a modified downstream product; no upstream endorsement is implied.

## ASFireWire — driver foundation

[ASFireWire](https://github.com/mrmidi/ASFireWire), copyright 2024–2026 ASFireWire
Project Contributors, provides the FireWire driver foundation under Apache-2.0.
Retained baseline: `ac8a124a683d2f8201cd14ee0d2de8265e4834f0`, with selectively
reviewed upstream correctness improvements and rewindDV-specific changes.

Downstream work includes the restricted DV/deck-control boundary, native app
integration, receive/evidence handling, lifecycle and generation safeguards,
metadata/verification workflows, and selective resource/topology hardening.
The release does not add ASFireWire audio-interface or SCSI product features.

The complete [Apache-2.0 license](ASFireWire-LICENSE.txt) and
[NOTICE](ASFireWire-NOTICE.txt) accompany the app and download. The NOTICE also
records Apple's public FWAddress API-layout attribution and behavioral references;
it does not claim those reference implementations are bundled.

## MediaInfoLib — selected DV metadata mappings

[MediaInfoLib](https://github.com/MediaArea/MediaInfoLib), by MediaArea.net SARL,
is credited for selected layouts/mappings adapted into bounded native Swift
decoders. The reviewed source is `File_DvDif.cpp` and `File_DvDif_Analysis.cpp`
at `6ce87668473b0591c323a66842c937aa1cf76bdf`.

These adaptations retain format/section guards, raw evidence and conflict
reporting. No MediaInfo runtime library is bundled. Its BSD 2-Clause copyright,
conditions and disclaimer are reproduced in [ThirdPartyNotices.txt](ThirdPartyNotices.txt).

## DVRescue — geometry and interoperability references

[DVRescue](https://github.com/mipops/dvrescue), from Moving Image Preservation
of Puget Sound and its contributors, is credited for the `tools/dvloupe` nominal
DV25 block-geometry adaptation at `5cead7a5dae4ec7ffdf24115c8e3bc6d9c05c033`.
The development tests also use its report schema and an interoperability fixture
at that revision; those test sources are not shipped in this binary package.

The DVRescue runtime, capture backend and merger are not bundled. The applicable
BSD 3-Clause copyright, conditions and disclaimer are reproduced in
[ThirdPartyNotices.txt](ThirdPartyNotices.txt).

## Distribution scope

This repository distributes binaries, documentation, branding assets and license
notices—not the rewindDV application source tree. The third-party permissions
and notices continue to apply to their respective components. Availability of
this download is not a grant of rights to third-party trademarks or standards.

IEC, IEEE and other standards are research references, not downloadable assets
in this repository. Sponsorship for standards purchases does not permit us to
redistribute their copyrighted contents.
