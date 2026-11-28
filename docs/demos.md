# Demonstrations

These selected clips are qualitative research examples that make individual behaviors easier to inspect. Metrics and protocols are recorded in the linked experiment notes. All published frames use synthetic animation from the [TA2.0 Animation Dataset](https://huggingface.co/datasets/neosapience/TA2.0_animation_dataset); no real-person or game footage is included.

## Korean full-face comparison

[Play the 3.84-second full-face comparison](../assets/demos/ta2-korean-fullface.mp4). It places Official Ditto's released-native motion stitch beside E350 routing `face21_lip_g2`, with the shared synchronized audio from the same benchmark condition. Both outputs use TA2 sample `clip_00209` (`ref_03160`, active motion, Korean), seed 1701, 96 frames at 25 fps, and a 1280x1280 source canvas. This is a qualitative pair; cross-model coverage and metrics are recorded in the benchmark notes.

## English E350 sample

[Play the two-second sample](../assets/demos/ta2-e350-english.mp4). It uses TA2 sample `clip_00271` (`ref_06067`, active motion, English) from 1-3 s of the dataset clip. The panels compare the TA2 original, audio-driven MotionDiT at epoch 350 with the frozen renderer, and a diagnostic ground-truth-motion replay. Additional rows vary audio-motion gain and select lower- or higher-opening reference frames. The speech track remains synchronized to its original excerpt.

## TA2 comparison sample

[Play the four-second comparison](../assets/demos/ta2-compare.mp4). It concatenates the already aligned 1-3 s excerpts from `clip_00035` (`ref_04068`, static motion, English) and `clip_05546` (`ref_07267`, active motion, English). The first is an intentionally difficult failure example: the baseline and gain/reference variants do not reproduce the original mouth timing or shape consistently. The second shows how the same controls behave on a different stylized character. This edit only concatenates the two excerpts and re-encodes the existing synchronized audio.

A longer 20-sample English montage is prepared as `ta2-e350-english20.mp4` for the repository's [Releases](https://github.com/p030610/AnimLip/releases) rather than tracked in Git.

## Controllable motion

[Open the full-size control diagram](../assets/previews/ta2-control.png).

The control diagram is an original schematic of the tested pipeline. Speech conditions the MotionDiT motion predictor, and a frozen renderer produces the animated result. Audio-motion gain and reference-frame choice were changed only as diagnostic controls. The comparison used one predicted motion sequence per clip across reference conditions, so reference changes probe the renderer and relative-motion composition rather than rerunning motion inference.

Across the 20 English clips, the tested 0.5x, 1x, and 2x gains had mouth-opening MAE 0.1139, 0.1126, and 0.1096. Choosing a more-open rather than less-open reference increased mean rendered opening by 0.2407 in all 20 clips. These measurements describe this cohort and setup; the controls are not calibrated user-facing units.

## Limitations

[Open the full-size limitations diagram](../assets/previews/ta2-limitations.png).

- The examples are deliberately close mouth crops. They illustrate motion behavior, not full-frame visual quality.
- The automated opening estimate is sensitive to stylized character geometry and should be read as a relative diagnostic signal.
- Gain can increase motion range without improving temporal agreement. In this experiment, median temporal correlation decreased from 0.443 at 0.5x to 0.275 at 2x.
- Reference selection can change pose, expression, and composition as well as mouth opening. The lower/higher references were selected from the same ground-truth clip for diagnosis, not as a deployable selection procedure.
- `clip_00035` is retained as a visible failure example; at several frames the generated variants remain open while the TA2 original is nearly closed.

## Provenance and attribution

The source clips are `videos/000/clip_00035.mp4`, `videos/000/clip_00209.mp4`, `videos/000/clip_00271.mp4`, and `videos/005/clip_05546.mp4` from the TA2.0 Animation Dataset. The dataset card releases its synthetic video under Apache-2.0 and identifies LongCat-Video-Avatar as the generator. The English comparison outputs were produced with MotionDiT epoch 350 and the frozen renderer, seed 1701, at 25 fps. The Korean pair uses the separately recorded Official Ditto and E350 routes named above.

TA2's embedded speech derives from these openly licensed corpora:

| Audio corpus | License |
|---|---|
| [Multilingual LibriSpeech (OpenSLR 94)](https://www.openslr.org/94/) | CC BY 4.0 |
| [The People's Speech (MLCommons)](https://huggingface.co/datasets/MLCommons/peoples_speech) | CC BY subsets, 2.0-4.0 |
| [VoxPopuli (Meta)](https://huggingface.co/datasets/facebook/voxpopuli) | CC0 1.0 |
| [LibriSpeech (OpenSLR 12)](https://www.openslr.org/12/) | CC BY 4.0 |
| [Zeroth-Korean (OpenSLR 40)](https://www.openslr.org/40/) | CC BY 4.0 |
| [FLEURS (Google)](https://huggingface.co/datasets/google/fleurs) | CC BY 4.0 |
| [YODAS (ESPnet)](https://huggingface.co/datasets/espnet/yodas) | CC BY 3.0 |
| [AMI Meeting Corpus (IHM)](https://groups.inf.ed.ac.uk/ami/corpus/) | CC BY 4.0 |
| [MInDS-14 (PolyAI)](https://huggingface.co/datasets/PolyAI/minds14) | CC BY 4.0 |

TA2's public metadata identifies the demonstrated clips as Korean or English but does not expose the upstream corpus on a per-clip basis, so all nine source credits are preserved here rather than guessing a narrower attribution. The audio was segmented, AAC-encoded, and muxed by TA2; our edits trim, concatenate where stated, and re-encode without changing speech content. See TA2's canonical [audio attribution page](https://huggingface.co/datasets/neosapience/TA2.0_animation_dataset/blob/main/ATTRIBUTION.md) for complete source and license notes.

The exact source hashes, export commands, decoded-playback checks, and inspected-frame contact sheet are retained in the private release evidence for this publication.
