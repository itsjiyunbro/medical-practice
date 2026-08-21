# Daily Paper Recommendations — 2026-08-19

## 검색 개요

- **연구 날짜(research date)**: 2026-08-19
- **실제 검색 창(search window)**: 2026-07-20 ~ 2026-08-19 (30일 창; 1일·7일 창에서는 결과가 0건이어서 확대)
- **검색 쿼리**: `chest radiograph deep learning multi-institution generalization`

## 코호트 개요 (코호트 수준 집계만; 환자 단위 값 없음)

- 총 272건의 흉부 X선 레코드, 고유 환자 153명
- 성별: 남 136 / 여 136 (균형)
- 연령: 평균 51.5세 (범위 9–87세)
- 촬영 자세: PA 184건, AP 88건
- 소견 라벨(상위): No Finding 145, Infiltration 21, Atelectasis 16, Nodule 7, Fibrosis 6, Effusion 6, Cardiomegaly 5, Pneumothorax 5 (다중 라벨 조합 다수 포함)
- 수집 기관: INST01(62), INST02(56), INST03(54), INST05(52), INST04(48) — 5개 기관에 고르게 분산
- 진료과: radiology(57), internal_medicine(57), cardiology(53), emergency(53), pulmonology(52)

## 선정 축 (Axes)

1. **기관 간 일반화** — 여러 기관/사이트에 걸친 모델 성능 전이 및 강건성
2. **라벨 잡음 / 주석 부족** — 픽셀 단위 주석 없이 자유 텍스트 판독문만 있는 상황에서의 학습
3. **설명 가능성** — 예측을 임상적으로 감사 가능하게 만드는 접근

## 채택 논문

### 1. CLEAR: an auditable foundation model for radiology grounded in clinical concepts
- **축**: 기관 간 일반화, 설명 가능성
- **관련성**: 우리 코호트는 5개 기관(INST01–05)에서 수집된 272건의 흉부 X선, 다중 소견 라벨을 갖고 있어 CLEAR가 검증한 다기관·다중 소견 환경과 구조적으로 유사함.
- **한계**: 우리 데이터는 272건 규모로 CLEAR의 외부 검증 규모(수십만 환자)에 비해 매우 작아 동일 성능을 재현·확인할 수 없음.
- 링크: https://doi.org/10.1038/s41551-026-01741-4

### 2. Grounding Radiology Report Findings into Medical Image Segmentation (CF2Seg)
- **축**: 기관 간 일반화, 라벨 잡음
- **관련성**: 우리 코호트의 판독문(report_text/clinical_info)은 픽셀 단위 주석 없이 자유 텍스트 소견만 기록하고 있어, CF2Seg가 다루는 '보고서만 있고 분할 주석은 없는' 상황과 정확히 일치함.
- **한계**: 우리 코호트에는 전문가 공간 주석(픽셀 마스크)이 전혀 없어 실제 분할 정확도를 검증할 수 없음.
- 링크: https://doi.org/10.1038/s41746-026-03051-0

### 3. QoQ-Med3: a multimodal reasoning foundation model for clinical analysis
- **축**: 기관 간 일반화, 설명 가능성
- **관련성**: 우리 코호트는 5개 기관, 5개 진료과에 걸쳐 수집되어 사이트 간 이질성이 존재하며, QoQ-Med3가 검증한 '기관 간 전이성/강건성' 평가 축이 바로 적용 가능함.
- **한계**: 우리 데이터는 흉부 X선 단일 모달리티만 있어 다중 모달리티 간 전이 성능 향상은 확인할 수 없음.
- 링크: https://doi.org/10.1038/s41746-026-02945-3

## 주의사항

이 추천은 자동 검색 및 코호트 수준 집계에 기반한 것으로, 실제 임상 적용 전 반드시 담당 의료진의 검토가 필요합니다 (physician review required).
