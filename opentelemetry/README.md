# OpenTelemetry Operator를 활용한 Spring 애플리케이션 모니터링

## 개요

Kubernetes 클러스터 환경에서 OpenTelemetry Operator를 활용하여 Spring 애플리케이션에 OpenTelemetry Java Agent를 자동으로 삽입하여 모니터링 설정

### 주요 구성 요소

- **OpenTelemetry Operator**: OpenTelemetry 컴포넌트 자동 관리
- **OpenTelemetry Java Agent**: Spring 애플리케이션에 자동 삽입되는 모니터링 에이전트

## 사전 요구사항

- Kubernetes 클러스터 (v1.19+)
- kubectl 설치 및 클러스터 접근 권한
- Spring Boot 애플리케이션 (Java 8+)

## OpenTelemetry Operator 설치

```bash
helm repo add open-telemetry https://open-telemetry.github.io/opentelemetry-helm-charts
helm repo update

helm install opentelemetry-operator open-telemetry/opentelemetry-operator \
  --namespace opentelemetry \
  --create-namespace \
  --values opentelemetry-operator-values.yaml
```

## OpenTelemetry Instrumentation 설정

### Instrumentation 역할

- OpenTelemetry Java Agent를 Spring 애플리케이션에 자동으로 삽입
- 특정 라벨(`app: java`)을 가진 Pod에만 적용
- 트레이스와 메트릭 수집을 위한 환경 변수 설정

### Spring Application 최소 설정

```yaml
# Pod 라벨과 어노테이션만 추가
metadata:
  labels:
    app: java # Instrumentation과 매칭되는 라벨
  annotations:
    instrumentation.opentelemetry.io/inject-java: "true"
    instrumentation.opentelemetry.io/instrumentation-name: "spring-instrumentation"
```
