# Score replay and settings

This note separates a score-level recomputation from a fresh upstream run. A score-level recomputation needs the original permitted inputs, frozen model or checkpoint, implementation revision, output receipts, and metric code. None of the historical research threads in this archive meet all of those conditions. The public status is therefore report-only unless a future release supplies all of those materials with explicit permissions.

## Verified historical check

The following CPU-only command was executed against the historical KoNet evaluation package. It generated a synthetic report and metric artifacts and passed 13 tests. It is recorded for audit only. The package and data are not part of this repository, so this is not a command that a clean checkout can run.

```powershell
python -m pytest tests/test_ko_offset_metrics.py -q -p no:cacheprovider
```

The historical package reported Python 3.10.11, PyTorch 2.5.1 with CUDA 12.1, NumPy 1.26.4, OmegaConf 2.3.0, Pydantic 2.13.5, and pytest 8.3.5. This environment record is descriptive rather than a supported lockfile.

## Recorded settings

| Thread | Settings preserved from the executed record | Replay decision |
| --- | --- | --- |
| KoNet and StableSyncNet | LatentSync revision `75a4a1733c7314a8f6bf092f1fbe4ced008cccd7`, seed 42, 16-frame pixel attention, embedding width 2048, AdamW learning rate `1e-5`, FP16 AMP, FP32 embedding cosine BCE, gradient clip 1.0, global validation and save interval 2500 steps | No score replay. The source package, split manifests, weights, and lawful held-out audio-video inputs are absent. An independent implementation must preserve the documented protocol and label its result as new. |
| TA2.0 benchmark | TA2.0 only, same-pair and cross-audio modes, frozen model assets, historical common-success subsets of 14 same-pair cases and 7 cross-audio cases for the five main arms | No score replay. The case roster, source media, generated outputs, benchmark wrapper, and score rows are absent. Do not infer a ranking from a fresh run with different coverage. |
| TA2.0 motion calibration | A train-only gain choice, a fixed 40-case validation comparison, 16 frames per case, and the same reference and audio within each compared condition | No score replay. The calibration code, selected checkpoint, roster, and reference assets are absent. |
| Teeth-visibility encoders | Wav2Vec2 Base and Whisper small sixth-layer features of width 768, Smooth L1, AdamW, batch size 64, seed 42, 100 epochs, early selection on validation MAE | No score replay. The labeler, split, regression head, selected checkpoints, and metric data are absent. TA2.0 augmentation was not run after the label-validation gate failed. |

## Official upstream sources required for new work

Use the official project pages and inspect the current release terms before downloading a source or weight. These links are sources of software or model material, not permission for this archive to redistribute them.

| System | Official source | Software license observed on 2026-11-28 | Weight condition |
| --- | --- | --- | --- |
| Ditto | [antgroup/ditto-talkinghead](https://github.com/antgroup/ditto-talkinghead) | [Apache-2.0](https://raw.githubusercontent.com/antgroup/ditto-talkinghead/main/LICENSE) | Download from the upstream release after checking each weight and component notice. No weight is included here. |
| LatentSync and StableSyncNet | [ByteDance/LatentSync](https://github.com/ByteDance/LatentSync) | [Apache-2.0](https://raw.githubusercontent.com/ByteDance/LatentSync/main/LICENSE) | Download from the upstream release after checking each weight and component notice. No weight is included here. |
| MuseTalk | [TMElyralab/MuseTalk](https://github.com/TMElyralab/MuseTalk) | [MIT](https://raw.githubusercontent.com/TMElyralab/MuseTalk/main/LICENSE) | Download from the upstream release after checking each weight and component notice. No weight is included here. |
| VideoReTalking | [OpenTalker/video-retalking](https://github.com/OpenTalker/video-retalking) | [Apache-2.0](https://raw.githubusercontent.com/OpenTalker/video-retalking/main/LICENSE) | Download from the upstream release after checking each weight and component notice. No weight is included here. |
| Wav2Vec2 Base 960h | [official model card](https://huggingface.co/facebook/wav2vec2-base-960h) | Apache-2.0 on the official model card | Obtain directly from the card. The model expects 16 kHz audio. |
| Whisper small | [openai/whisper](https://github.com/openai/whisper) | [MIT](https://raw.githubusercontent.com/openai/whisper/main/LICENSE) for the official code and weights | Obtain directly from OpenAI and retain the upstream notice. |

The component notices above do not grant rights to third-party data, portrait images, voices, or generated media. A derivative video may require permissions beyond the code or weight license.
