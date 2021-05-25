# loginsight-helm-fluentd

This repo contains helm charts to push Kubernetes Logs to vRealize Log Insight using fluentd daemonset. 

# Pre-requisities 

You need to have following pre-requisties 

1.	vRealize LogInsight Cloud API Token
2.	Helm Version = '3.x'
3.  Admin access to the Kubernetes Cluster

# Installing the Chart - Procedure 1 

## Add Chart Repo 
```
helm repo add loginsightcloud https://munishpalmakhija.github.io/loginsight-cloud-helm-fluentbit/
```


## Get Values file in your working directory 
```
helm show values loginsightcloud/loginsight-cloud-helm-fluentbit  > values.yaml
```

## Update Values file with API Token and other relevant details.  
```
cat values.yaml
```

## Install Chart.  
```
helm install vrlic-fluentbit-helm-test loginsightcloud/loginsight-cloud-helm-fluentbit -f values.yaml
```

## Verify Kubernetes Pods  
```
kubectl get pods -A | grep vrlic-fluentbit-helm-test
```

## Verify Helm Release 
```
helm list
```

# Installing the Chart - Procedure 2

## Add Chart Repo 
```
helm repo add loginsightcloud https://munishpalmakhija.github.io/loginsight-cloud-helm-fluentbit/
```


## Install Chart by setting values during run time.  

```
helm install vrlic-fluentbit-helm-test loginsightcloud/loginsight-cloud-helm-fluentbit/ --set  vrlic.apikey=SETME --set tag.environment=tanzu_k8s_grid
```

## Verify Kubernetes Pods  
```
kubectl get pods -A | grep vrlic-fluentbit-helm-test
```
## Verify Helm Release 
```
helm list
```