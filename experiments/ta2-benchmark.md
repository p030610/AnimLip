# TA2.0 다섯 모델 벤치마크

## 스냅샷

이 장은 [TA2.0](https://huggingface.co/datasets/neosapience/TA2.0_animation_dataset) test 80클립의 완료 상태와 품질 표본을 분리해 기록한다. 완료 상태는 2026-11-27 22:27 KST 스냅샷이고 정량값은 같은 날 22:15 KST에 확보한 완성 영상 스냅샷이다. 동일 음성과 교체 음성은 독립 실행으로 집계했다. 성공, 실패, 미완료의 분모는 각각 80이며 수치는 [상태 CSV](tables/ta2-inference-status-20261127.csv)에 있다.

| 모델 | 동일 음성 성공 | 동일 음성 실패 | 동일 음성 미완료 | 교체 음성 성공 | 교체 음성 실패 | 교체 음성 미완료 |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| E350 | 69 | 11 | 0 | 69 | 11 | 0 |
| 공식 Ditto | 69 | 11 | 0 | 69 | 11 | 0 |
| MuseTalk 1.5 | 18 | 62 | 0 | 18 | 62 | 0 |
| VideoReTalking | 15 | 65 | 0 | 8 | 48 | 24 |
| LatentSync 1.5 | 43 | 37 | 0 | 43 | 37 | 0 |

## 공통 성공과 짝비교

다섯 모델 공통 성공 표본은 동일 음성 14클립, 교체 음성 7클립이다. 이 표본의 정량값은 공통 성공 조건을 만족한 영상의 순서일 뿐 전체 80클립의 종합 순위가 아니다. 동일 음성에서 E350과 상대 모델의 공통 성공 수는 공식 Ditto 69, MuseTalk 18, VideoReTalking 15, LatentSync 43이다. 공식 Ditto 짝비교의 개구와 입 닫힘 유효 표본은 67이며 LatentSync 짝비교의 해당 유효 표본은 42다. MuseTalk과 VideoReTalking의 해당 짝비교 수는 각각 18과 15다. 교체 음성의 짝별 수는 이 스냅샷에서 별도로 확정하지 않았으므로 다섯 모델 공통 수 7과 혼용하지 않는다.

다섯 모델 공통 표본의 정량값은 22:15 KST 스냅샷의 [공통 표본 CSV](tables/ta2-five-model-common-20261127.csv)에 분리했다. 동일 음성에는 PSNR, VGG-LPIPS, 개구 MAE, 입 닫힘 F1, FID, FVD-16을 기록했다. 교체 음성에는 대응 GT가 없으므로 FID와 FVD-16만 기록했다.

## 편향과 실패

전체 roster는 한국어 활발, 한국어 정적, 영어 활발, 영어 정적이 각 20클립으로 균형을 맞췄다. 22:15 KST 네 모델 공통 표본의 구성은 동일 음성에서 4, 0, 4, 7이고 교체 음성에서 4, 0, 1, 3이다. 다섯 모델 공통 표본은 LatentSync를 포함하는 별도 교집합 14와 7이다. 공통 표본에는 한국어 정적 클립이 없었다. 따라서 공통 성공 표본의 좋은 수치와 모델별 완료율을 분리해 읽어야 한다.

SyncNet-v2는 TA2.0 사전 검증 기준을 충족하지 않아 순위 산정에 넣지 않았다. VideoReTalking의 교체 음성에는 미완료가 남아 있다. 실패 영상은 품질값을 만들지 않았으므로 성공한 사례만으로 전체 순위를 만들지 않는다.

## 비교 기준

외부 구현의 공개 계보는 [Ditto](https://huggingface.co/digital-avatar/ditto-talkinghead), [MuseTalk](https://github.com/TMElyralab/MuseTalk), [VideoReTalking](https://github.com/OpenTalker/video-retalking), [LatentSync](https://github.com/bytedance/LatentSync)에서 확인할 수 있다.
