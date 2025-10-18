# Kubernetes Development Environment

> **k3d**를 활용한 로컬 Kubernetes 개발 환경에서 실제 운영 환경을 모방한 테스트 및 연습 공간

## 🚀 개요

이 저장소는 로컬 환경에서 **k3d** (Kubernetes in Docker)를 활용하여 실제 운영 환경과 유사한 Kubernetes 클러스터를 구축하고, 다양한 Kubernetes 리소스와 운영 도구들을 실습할 수 있는 개발 환경입니다.

> 🌍 **크로스 플랫폼 호환**: Windows, macOS, Linux 환경에서 동일하게 동작하며, 개발 환경 변경 시에도 설정을 그대로 이식할 수 있습니다.

## 🎯 목표

- **실무 중심 학습**: 실제 운영 환경에서 사용되는 패턴과 도구들을 로컬에서 경험
- **안전한 실험**: 로컬 환경에서 자유롭게 실험하고 실패해도 안전한 환경 제공
- **운영 역량 강화**: Kubernetes 운영에 필요한 실무 스킬과 노하우 습득

## 🛠️ 주요 구성 요소

### 클러스터 관리

- **k3d**: 경량화된 Kubernetes 클러스터 (Docker 기반)
- **kubectl**: Kubernetes 클러스터 관리 도구

### 모니터링 & 관찰성

- **OpenTelemetry Operator**: 분산 추적 및 메트릭 수집
- **Grafana**: 시각화 및 대시보드
- **Loki**: 로그 수집 및 저장
- **Mimir**: 메트릭 저장 및 쿼리
- **Tempo**: 분산 트레이싱 저장

### 개발 도구

- **Spring Boot**: 마이크로서비스 애플리케이션 개발
- **Docker**: 컨테이너화 및 이미지 빌드

## 📁 프로젝트 구조

```
k8s-dev/
├── opentelemetry/          # OpenTelemetry 모니터링 설정
│   └── README.md          # OpenTelemetry Operator 가이드
└── README.md            # 이 파일
```

> 📝 **참고**: 프로젝트 구조는 지속적으로 확장되며, 새로운 모니터링 스택과 애플리케이션 설정이 추가될 예정입니다.

## 🚦 시작하기

### 사전 요구사항

- Docker Desktop
- kubectl
- k3d CLI

### 클러스터 생성

```bash
# k3d 클러스터 생성
kubectl cluster create dev-cluster --port "8080:80@loadbalancer"

# 클러스터 정보 확인
kubectl cluster-info
```

## 🎓 학습 경로

1. **기본 환경 구축** - k3d 클러스터 생성 및 기본 설정
2. **모니터링 스택** - Grafana, Loki, Mimir, Tempo를 활용한 관찰성 구축
3. **애플리케이션 배포** - Spring Boot 마이크로서비스 배포 및 관리
4. **운영 실습** - 로그 수집, 메트릭 모니터링, 트러블슈팅

## 🔧 실무 시나리오

- **마이크로서비스 배포**: Spring Boot 애플리케이션의 Kubernetes 배포
- **자동 모니터링**: OpenTelemetry Operator를 통한 자동 instrumentation
- **통합 관찰성**: Grafana를 통한 로그, 메트릭, 트레이스 통합 시각화
- **분산 추적**: Tempo를 활용한 서비스 간 호출 추적 및 성능 분석

## 📚 참고 자료

- [k3d 공식 문서](https://k3d.io/)
- [Kubernetes 공식 문서](https://kubernetes.io/docs/)
- [OpenTelemetry 문서](https://opentelemetry.io/docs/)
