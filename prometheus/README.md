## 创建prometheus

在node2节点mkdir -p /data/k8s/prometheus
kubectl apply -f prometheus-pv-pvc.yaml

创建configmao kubectl apply -f prometheus-cm.yaml

kubectl apply -f prometheus-rbac.yaml

kubectl apply -f prometheus-deploy.yaml

kubectl get pod -n kube-mon

