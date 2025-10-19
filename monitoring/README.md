# Monitoring

Grafana 모니터링 스택을 위한 Helm values 설정 파일들이 포함된 디렉토리입니다.

## Grafana

### values 파일 생성

```bash
curl -o monitoring/grafana-values.yaml https://raw.githubusercontent.com/grafana/helm-charts/main/charts/grafana/values.yaml
```

### Grafana 설치

```bash
helm install grafana grafana/grafana -f monitoring/grafana-values.yaml --namespace monitoring --create-namespace
```

## Mimir

### values 파일 생성

```bash
helm show values grafana/mimir-distributed > monitoring/mimir-values.yaml
```

### Mimir 설치

```bash
helm install mimir grafana/mimir-distributed -f monitoring/mimir-values.yaml --namespace monitoring
```

## Loki

### values 파일 생성

```bash
helm show values grafana/loki-distributed > monitoring/loki-distributed-values.yaml
```

### Loki 설치

```bash
helm install loki grafana/loki-distributed -f monitoring/loki-distributed-values.yaml --namespace monitoring
```

## Tempo

### values 파일 생성

```bash
helm show values grafana/tempo-distributed > monitoring/tempo-distributed-values.yaml
```

### Tempo 설치

```bash
helm install tempo grafana/tempo-distributed -f monitoring/tempo-distributed-values.yaml --namespace monitoring
```
