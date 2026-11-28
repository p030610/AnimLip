# 실험 기록

이 디렉터리는 AnimLip 연구에서 재생성 가능한 수치와 제한된 결론만 모은 공개용 기록이다. 각 장은 측정 시점, 표본 범위, 실패를 함께 적는다. 숫자는 서로 다른 표본이나 목적의 실험 사이에서 순위를 만들기 위해 쓰지 않는다.

## 읽는 순서

| 기록 | 범위 | 상태 |
| --- | --- | --- |
| [LNet과 SyncNet](lnet-syncnet.md) | 재구성, 동기화, 규모, VGG, GAN, LVFace 축 | 통합 연기와 후속 평가 필요 |
| [KoNet](konet.md) | 한국어 오프셋 점수 비교 | 완료된 held-out 점수 재계산 |
| [Ditto와 MotionDiT](ditto-motiondit.md) | 공식 사전학습 기준과 E350 | 제한된 HDTF 비교 |
| [TA2.0 벤치마크](ta2-benchmark.md) | 다섯 모델의 완료 상태와 공통 성공 표본 | 2026-11-27 고정 스냅샷 |
| [치아 노출](teeth-visibility.md) | 오디오 인코더 회귀와 TA2.0 라벨 적격성 | 2026-11-28 고정 스냅샷 |

## 수치 재생성 규약

표는 원시 영상, 원시 음성, 가중치, 실행 로그를 포함하지 않는다. 대신 이 저장소의 범위가 제한된 CSV에 반올림 전 집계값과 분모를 남긴다. 각 CSV는 해당 장에서 정한 날짜와 스냅샷을 다시 읽어 만든 공개용 전사본이다. 표를 갱신할 때는 같은 스냅샷 시각, 같은 분모, 같은 성공 정의를 함께 갱신해야 한다.

외부 계보는 공개 upstream으로만 연결한다. 데이터셋은 [TA2.0](https://huggingface.co/datasets/neosapience/TA2.0_animation_dataset), 비교 기준은 [Ditto](https://huggingface.co/digital-avatar/ditto-talkinghead), [VideoReTalking](https://github.com/OpenTalker/video-retalking), [MuseTalk](https://github.com/TMElyralab/MuseTalk), [LatentSync](https://github.com/bytedance/LatentSync)에서 확인할 수 있다. 이 기록은 upstream 배포물이나 데이터의 재배포 권한을 뜻하지 않는다.

## 공개 범위

공개용 기록에는 요약 문장, 집계표, 측정 규약, 공개 upstream 링크만 둔다. 개인 식별자, 원본 파일명, 장비 경로, 원시 관측치, 모델 가중치, 실행 명령, 로그는 넣지 않는다.
