# 일일 논문 추천 — 2026-08-21

## 검색 개요
- **연구 기준일**: 2026-08-21 (Asia/Seoul 기준 어제)
- **실제 검색 범위**: 1일(08-21~08-21) → 결과 없음 → 7일(08-15~08-21) → 결과 없음 → 30일(2026-07-23~2026-08-21) 확대 후 3편 이상 확보, 검색 종료
- **검색 쿼리**: `chest X-ray multi-label disease classification deep learning` (기본), 보조로 `chest radiograph thoracic disease diagnosis AI`, `pulmonary nodule cardiomegaly pleural effusion detection external validation` 사용
- Nature, Nature Medicine, Nature Communications, Nature Biomedical Engineering, npj Digital Medicine, The Lancet Digital Health, Radiology, Radiology: AI, European Radiology, Medical Image Analysis (OpenAlex) 및 MICCAI/IPMI/CVPR/NeurIPS/ICLR (arXiv)를 통해 검색. arXiv 계열 소스는 30일 검색 시 요청 제한(HTTP 429)으로 결과를 받지 못함.

## 코호트 개요 (환자 단위 값 제외)
- 총 272건 검사, 153명 환자
- 성별: 남 136건(평균 연령 약 48.7세), 여 136건(평균 연령 약 54.3세)
- 촬영 자세: PA 184건, AP 88건
- 소견 분포: No Finding 145건이 최다, 이어서 Infiltration(21), Atelectasis(16), Nodule(7), Fibrosis(6), Effusion(6), Cardiomegaly(5), Pneumothorax(5) 등 다수의 소견이 저빈도로 공존하며 일부는 다중 라벨(예: Effusion+Infiltration 5건)로 기록됨
- 전반적으로 단일 우세 소견(No Finding) 외 나머지는 소수 클래스가 롱테일 형태로 분포하는 다중 라벨 흉부 X-ray 데이터셋 특성을 보임

## 선정 축 (axes)
1. **기관 간 일반화** — 다기관 외부 검증, 재현성 문제를 다루는 논문
2. **라벨 잡음 / 데이터 부족 보완** — 저품질·부족 데이터, 노이즈 필터링, 데이터 증강을 다루는 논문
3. **저빈도 질환 성능** — 클래스 불균형, 롱테일 소견에서의 성능 저하를 다루는 논문

## 추천 논문

### 1. A foundation model for acute abdomen diagnosis stratification and triage on noncontrast CT (Nature Communications)
- **축**: 기관 간 일반화, 판독의-AI 협업
- 3개 독립 외부 코호트(2528명)에서 검증하고 다중판독자 교차연구로 판독 정확도·속도 개선을 정량화한 대규모 실증 연구.
- 우리 데이터: 다중 소견 공존 구조와 판독 보조 도구 평가 설계가 참고할 만하나, 대상 장기(복부 CT)가 달라 직접 근거는 아님.
- 링크: https://doi.org/10.1038/s41467-026-76634-w

### 2. UniMedDiff: a knowledge-enhanced diffusion model for medical image generation from clinical reports (npj Digital Medicine)
- **축**: 데이터 부족 보완, 라벨 잡음
- 임상 보고서 기반 확산 모델로 흉부 X-ray를 포함한 11개 병리 영상을 합성하고, 1% 실데이터 증강만으로 분류 성능을 거의 원본 수준까지 회복.
- 우리 데이터: No Finding 145건 대비 결절 7건, 기흉 5건 등 저빈도 소견이 많아 데이터 증강 전략이 실질적으로 검토할 가치가 있음.
- 링크: https://doi.org/10.1038/s41746-026-03135-x

### 3. Multicenter evaluation of four large language models for automated spine imaging diagnosis (npj Digital Medicine)
- **축**: 기관 간 일반화, 저빈도 질환 성능
- 3개 기관 20,277건 판독문으로 4개 LLM을 비교, 저빈도 질환에서 정밀도가 19~42%p 하락하는 롱테일 문제를 정량적으로 제시.
- 우리 데이터: 유사한 저빈도 소견 불균형 구조를 가지고 있어, 동일한 성능 저하 패턴이 재현되는지 확인할 가치가 있음. 척추 영상 대상이라 흉부 X-ray에 대한 직접 근거는 아님.
- 링크: https://doi.org/10.1038/s41746-026-03133-z

## 검토 안내
위 추천은 자동 검색과 코호트 통계를 기반으로 한 초안이며, **임상적 적용 전 반드시 담당 의료진의 검토가 필요합니다.**
