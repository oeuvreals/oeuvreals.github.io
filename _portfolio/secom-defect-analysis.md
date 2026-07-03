---
title: "SECOM 반도체 웨이퍼 불량 예측"
excerpt: "극심한 불균형·약신호 센서 데이터에서 누수 없이 정직하게 불량을 예측하고 핵심 신호를 해석한 end-to-end ML 분석."
tags:
  - scikit-learn
  - imbalanced data
# header:
#   teaser: /assets/images/secom-thumb.png   # 썸네일 이미지를 넣으면 이 줄들의 # 를 지우세요
date: 2026-06-22
---

## 개요

반도체 제조 센서 데이터(UCI SECOM, 1,567 웨이퍼 × 590 센서, Fail 6.64%)로
웨이퍼 **불량(Fail)을 예측**하고, 어떤 센서 신호가 불량과 연결되는지를
설명 가능한 형태로 규명한 분석입니다.

## 핵심

- **파이프라인**: 데이터 진단 → 전처리(누수 방지) → 피처 선별 → 모델 → SHAP 해석 → what-if 시뮬레이션
- **모델**: XGBoost + SMOTE (129 피처, threshold 0.10)
- **태도**: "높은 정확도"가 아니라, 약신호·불균형 데이터에서 **정직하게 측정하고 신호를 검증·해석하는 설계**에 집중

## 링크

- [GitHub 저장소](https://github.com/oeuvreals/SECOM_defect_analysis)
