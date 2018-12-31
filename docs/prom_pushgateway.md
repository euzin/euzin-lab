# Prometheus pushgateway 설정 

- prometheus pushgateway 를 사용 하면 scrape 하기 애매한 메트릭을 push 할 수 있다. 

## 설치 
```
go get github.com/prometheus/pushgateway
```
    
## 설정

prometheus.yml : 
``` 
  - job_name: "pushgateway"
    scrape_interval: 5s
    honor_labels: true
    static_configs:
    - targets: ['localhost:9091']
```

## 푸쉬 예제 

```
echo "some_metric 3.14" | curl --data-binary @- localhost:9091/metrics/job/pushgateway
```

