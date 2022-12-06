#

Kubernetes CronJob
==================

## Inhalt
* [Einleitung](#einleitung)
* [Kubernetes CronJob](#kubernetes-cronjob)
* [Summary](#summary)


## Einleitung
Im Repository [deegree-k8s-helm](https://github.com/enatdvmv/deegree-k8s-helm) haben wir eine deegree Webapp mit zwei WebService in einem Kubernetes Cluster deployed. Auf dem Cluster werden wir jetzt noch einen Kubernetes CronJob anlegen, der regelmäßig Request gegen die WebServices ausführt.


## Kubernetes CronJob
Legen wir den CronJob mit *helm* über einen [Helm-Chart](helm-chart/sample-cronjob) an.
```
kubectl config use-context degree
helm lint sample-cronjob
helm upgrade --install sample-cronjob ./ sample-cronjob --namespace deegree  --create-namespace
```
Und schauen uns auf dem Cluster um.
```
kubectl get cronjob deegreecronjob
kubectl get pods
```
Jedes Mal, wenn der Cron schedule ausgeführt wird, wird ein neuer Pod erstellt, der die definierten Aufgaben ausführt. Was er ausführt, das können wir uns in den *logs* ansehen.
```
kubectl logs pod-name
```


## Summary
Sample Kubernetes CronJob. 
