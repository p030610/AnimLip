# Reproducibility boundary

This repository is a documented research archive. It includes aggregate results and attributed edited TA2.0 examples. Training code, checkpoints, raw datasets, unedited source media, raw experiment reports, manifests, and score rows are not included. A result is reproducible from this archive only when the required lawful inputs, exact implementation, and score procedure are independently available. The distinction matters because rerunning a named upstream model is not enough to recreate a historical score.

The study summaries are in [the experiment index](../experiments/index.md). The executable status, preserved settings, and verified commands are in [the score replay note](score-replay.md). Data and redistribution conditions are in [the data and licenses note](../docs/data-and-licenses.md).

## What each thread supports

| Thread | Provenance in this archive | What a new researcher can rerun | Historical score status |
| --- | --- | --- | --- |
| LNet and SyncNet | [LNet and SyncNet record](../experiments/lnet-syncnet.md) | No executable source is released here. Independent work requires a lawful replacement dataset and a newly implemented protocol. | Report-only. The archived measurements cannot be recomputed from this repository. |
| KoNet and StableSyncNet | [KoNet record](../experiments/konet.md) and the official [LatentSync source](https://github.com/ByteDance/LatentSync) | StableSyncNet can be independently trained or evaluated only after pinning the upstream revision, obtaining lawful inputs, and implementing the recorded held-out protocol. | Report-only for the historical tables. A CPU-only metric-test command was verified on the historical package, but that package and its inputs are not published here. |
| MotionDiT and frozen renderer | [MotionDiT record](../experiments/ditto-motiondit.md) and the official [Ditto source](https://github.com/antgroup/ditto-talkinghead) | Fresh qualitative inference may be attempted with a reviewed upstream revision, its separately obtained weights, and lawful input media. | Report-only. The study checkpoint, renderer integration, roster, and scorer are not released. |
| TA2.0 multi-model benchmark | [TA2.0 benchmark record](../experiments/ta2-benchmark.md) and the four official baseline sources linked in the replay note | A fresh baseline run is possible only after separately downloading TA2.0 and the required model assets. Record coverage and failures rather than substituting outputs. | Report-only. The locked cases, model receipts, outputs, and metric rows are not released, so a rerun cannot claim to reproduce the reported scores. |
| TA2.0 motion calibration | [motion calibration record](../experiments/ta2-benchmark.md) | The public TA2.0 card can be downloaded under its stated terms. The calibration implementation, frozen checkpoint, and selection roster are unavailable. | Report-only. |
| Teeth-visibility encoder comparison | [teeth-visibility record](../experiments/teeth-visibility.md), official [Wav2Vec2 model card](https://huggingface.co/facebook/wav2vec2-base-960h), and official [Whisper source](https://github.com/openai/whisper) | The encoders can be obtained from their owners. The labeler, historical sample split, training head, and scorer are not released. | Report-only. The experiment rejected adding TA2.0 labels because its validation gate was not met. |

## Rules for an independent rerun

Pin every upstream repository and downloaded weight to a recorded commit, tag, or content hash before execution. Retain the upstream license and model-card terms with that pin. Use only media and data that you are authorized to process. Do not substitute a differently trained weight, changed preprocessing, an overlapping test set, or a partial-success subset while calling the result a reproduction.

For any fresh run, write a machine-readable receipt containing the upstream revision, weight identifier and license, input-source authorization, preprocessing version, seed, requested and completed cases, failure reason for every missing case, metric version, and aggregation rule. Publish derived numbers only when the input and output rights permit it.

The repository has no command that downloads or reconstructs restricted inputs. The selected public demonstration is TA2.0-only and its per-clip attribution is maintained in [the demonstration note](../docs/demos.md).

## Known limits

The reported benchmark coverage is not a leaderboard. Methods can fail on different cases, so all-method complete-case summaries and pairwise summaries answer different questions. The TA2.0 test set was already exposed during prior research and is therefore historical evaluation evidence rather than a fresh final test. The motion-calibration result is a fixed validation comparison and does not establish generalization to unseen characters. The encoder comparison uses a limited held-out set and does not establish a general speech-encoder ranking.
