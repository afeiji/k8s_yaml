## 创建prometheus

在node2节点

mkdir -p /data/k8s/prometheus

kubectl apply -f prometheus-pv-pvc.yaml

创建configmap 

kubectl apply -f prometheus-cm.yaml

kubectl apply -f prometheus-rbac.yaml

kubectl apply -f prometheus-deploy.yaml

kubectl get pod -n kube-mon

