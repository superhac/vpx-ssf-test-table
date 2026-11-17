# SSF Speaker Test

A Visual Pinball X utility table for checking that a 7.1 Surround Sound Feedback (SSF) cabinet is wired and configured correctly. It plays a test sound on one speaker at a time and shows the active speaker on the backglass.

![Speakers](https://img.shields.io/badge/output-7.1%20SSF-orange)

## Contents

| File | Purpose |
|---|---|
| `SSF_Speaker_Test.vpx` | The table (script embedded) |
| `SSF_Speaker_Test.directb2s` | Backglass: cabinet diagram that highlights the active speaker |
| `music/ssf_test_left.mp3` | Pink-noise pulses on the left channel only (front left test) |
| `music/ssf_test_right.mp3` | Pink-noise pulses on the right channel only (front right test) |

## Installation

1. Download the zip from the [Releases](../../releases) page.
2. Extract it into your tables folder. Keep the files together: the backglass and the `music` folder must sit next to the `.vpx`.

## VPX settings

| Setting | Value |
|---|---|
| Playfield sound output mode | **SSF** |
| Playfield audio device | A 7.1 device, opened with **8 channels** |
| Backglass sound output mode | Stereo (2 channels), not "front left only" |
| Backglass | B2S Server (Windows) or the VPX **B2S plugin** enabled |

## Controls

| Input | Action |
|---|---|
| Left flipper | Previous speaker |
| Right flipper | Next speaker |
| Plunger | Change the playfield test sound (knocker, bumper, ball roll) |

## Speaker map

The speakers are tested in this order. Channel numbers follow the SDL 7.1 order used by VPX.

| Speaker | Channel | Location in the cabinet | How the table reaches it |
|---|---|---|---|
| Front Left | 0 | Backbox, left | Backglass output (music file, left channel) |
| Front Right | 1 | Backbox, right | Backglass output (music file, right channel) |
| Side Left | 6 | Head end (near backbox), left | Table sound, pan −1, fade −1 |
| Side Right | 7 | Head end, right | Table sound, pan +1, fade −1 |
| Back Left | 4 | Player end (flippers), left | Table sound, pan −1, fade +1 |
| Back Right | 5 | Player end, right | Table sound, pan +1, fade +1 |

Center (ch 2) and LFE (ch 3) are not used in SSF mode and cannot be reached from a table script.

## Troubleshooting

- **No sound from the front speakers:** check the VPX log for `Failed to stream music`. The `music` folder must be next to the table.
- **Sounds come out of the wrong speakers:** the playfield device is probably opening with fewer than 8 channels (for example as 5.1). Check the device's speaker configuration in your OS. Otherwise, check the physical wiring against the speaker map above.
- **No backglass:** make sure the B2S Server is installed, or the B2S plugin is enabled, and that the `.directb2s` has the same name as the `.vpx`.

## Releases

Pushing a tag starting with `v` (for example `v1.0.0`) runs the release workflow. It zips every file in the repository into `SSF_Speaker_Test/` and attaches the zip to a GitHub release. You can also start it from the Actions tab and enter a tag.

## Credits

Based on the VPX example table by fuzzel, jimmyfingers, jpsalas, toxie and unclewilly, with contributions from zany, djrobx, ninuzzu, rothbauerw and arngrim.
