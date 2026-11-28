# 치아 노출 회귀

## 결론

2026-11-28 스냅샷에서 TA2.0 기반 입 안쪽과 치아 후보 라벨은 학습 품질 기준을 충족하지 못했다. 따라서 이 라벨은 두 오디오 회귀기의 학습에 포함하지 않았다. 데이터셋 계보는 [TA2.0](https://huggingface.co/datasets/neosapience/TA2.0_animation_dataset)에서 확인할 수 있다.

판독 가능한 validation 33장 기준 치아 후보의 정밀도는 82.6%와 재현율은 95.0%였다. 정밀도 기준 85%에 미달했고 스타일별 양성과 음성 표본도 작았다. 이 결과는 TA2.0 오디오와 영상의 동기 품질을 판정한 결과가 아니다.

## 기존 자료 회귀 비교

동일한 test 118클립과 6,893프레임에서 고정 오디오 인코더를 비교했다. 두 모델의 수치와 분모는 [회귀 CSV](tables/teeth-regression-20261128.csv)에 있다.

| 지표 | Wav2Vec2 Base | Whisper small |
| --- | ---: | ---: |
| 최저 validation MAE | 0.3614 | 0.3476 |
| test MAE | 0.3589 | 0.3653 |
| test Pearson r | 0.2930 | 0.2857 |
| test Smooth L1 | 0.0885 | 0.0837 |
| 치아 노출 전환 F1 | 0.3630 | 0.3537 |

Whisper small의 validation MAE는 낮았지만 같은 test 프레임에서는 Wav2Vec2 Base의 MAE와 상관이 더 좋았다. test MAE 차이의 10,000회 클립 재표본화 95% 구간은 -0.0039에서 +0.0167로 0을 포함했다. 이 스냅샷의 추론 선택은 Wav2Vec2 Base를 유지하는 것이다.

## 제한

이 비교는 보관된 두 test 그룹에 조건부다. 긴 학습의 train 오차 감소는 validation 개선으로 이어지지 않았고 선택 epoch도 이른 시점이었다. 두 인코더의 일반 우열이나 사람 지각 품질은 이 표에서 주장하지 않는다.
