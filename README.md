# Centralized Observability System (LGTM + Alloy)

초당 10,000 RPS 수준의 트래픽 환경을 기준으로 시스템 안정성을 검증하고,  
장애 발생 시 추적 시간(MTTR)을 단축하기 위해 구축한 통합 관측성(Observability) 아키텍처입니다.

Prometheus, Loki, Tempo, Grafana(LGTM 스택)를 기반으로 메트릭, 로그, 트레이스를 중앙 집중화하여 수집 및 시각화합니다.

> Data is collected from EKS clusters via Grafana Alloy and processed in a centralized LGTM stack.

---

## Architecture Overview

- Fault Isolation: 서비스 VPC(EKS)와 모니터링 시스템을 Central VPC로 분리하여, 운영망 장애 시에도 관제망이 유지되도록 설계
- OTel 기반 통합 파이프라인: EKS 환경에서 Grafana Alloy를 활용한 수집 파이프라인을 설계하고, 메트릭/로그/트레이스를 중앙 LGTM 스택으로 전달하도록 구성
- Drill-down Dashboard: 사용자 체감 지표부터 트레이스 기반 원인 분석까지 단계적으로 추적 가능한 관측 구조 설계

---

## Tech Stack

- Metrics: Prometheus
- Logs: Grafana Loki
- Traces: Grafana Tempo
- Collector: Grafana Alloy (OpenTelemetry Collector)
- Visualization: Grafana
- Alerting: Prometheus alert rules

---

## Directory Structure

```text
.
├── docker-compose.yml
├── config/
│   ├── prometheus.yml
│   ├── loki.yaml
│   ├── tempo.yaml
│   └── alert.rules.yml
└── README.md
