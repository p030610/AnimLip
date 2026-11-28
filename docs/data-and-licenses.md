# Data and licenses

This archive includes aggregate research records and attributed edited TA2.0 examples. It does not include raw datasets, checkpoints, source snapshots, raw reports, manifests, or private implementation code. The repository [MIT license](https://github.com/p030610/AnimLip/blob/main/LICENSE) applies to this archive's original documentation and does not relicense third-party material.

## Data sources

| Source | Official terms or card | Archive treatment |
| --- | --- | --- |
| TA2.0 animation dataset | The official [TA2.0 dataset card](https://huggingface.co/datasets/neosapience/TA2.0_animation_dataset) identifies the dataset as synthetic video and lists Apache-2.0. | No dataset copy is included. The only public media candidates are TA2.0-derived and require the per-clip attribution in [the demonstration note](demos.md). The dataset-card license is distinct from the license of each model, encoder, renderer, or third-party component used to make a result. |
| HDTF | The official [HDTF dataset repository](https://github.com/Darius-H/HDTF_dataset) states CC BY 4.0 for the dataset. Its separate [software repository](https://github.com/MRzzm/HDTF) carries GPL-3.0. | The archive records aggregate HDTF results only. Obtain source material from the original provider under the current dataset terms. The software license does not determine the dataset terms. |
| VoxCeleb2 | The official [VoxCeleb2 page](https://www.robots.ox.ac.uk/~vgg/data/voxceleb/vox2.html) states that its metadata is CC BY-SA 4.0 and that the original URL, audio, video, and identifying metadata downloads are no longer available there. | The archive records aggregate VoxCeleb2 results only. Obtain source material from the original provider under the current dataset terms. The metadata license is not treated as permission to redistribute underlying audiovisual material. |

## Model and tool material

No checkpoint, source snapshot, or dependency wheel is bundled. The [replay note](../reproducibility/score-replay.md) records official upstream locations and the software license observed for Ditto, LatentSync, MuseTalk, VideoReTalking, Wav2Vec2, and Whisper. Obtain each item from its owner, pin the selected version, and keep its current license and notices with the run.

Third-party rights remain with their respective owners. Code, weights, data, face analysis, audio processing, rendering assets, portraits, voices, source recordings, and third-party outputs can each carry separate terms. Review every downloaded asset and component notice before a fresh run or redistribution.

## Demonstrations and attribution

The published examples use TA2.0 only. [The demonstration note](demos.md) is the authoritative per-asset record for the source, embedded audio, transformation, and publication decision. It should be read together with the TA2.0 dataset card.

If a later asset lacks a documented source, embedded-audio basis, or redistribution authorization, it must not be added to the archive. The same rule applies to derived previews, still frames, and alternate encodings.
