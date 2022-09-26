**Multi-broker Kafka setup over Kubernetes**

In this repo, I'm gonna share my deployment of the Multi-broker Kafka installation and configuration. Let's assume we have Kubernetes installed already ;). 

Lets build the pods with the below order. 
- Zookeeper & zookeeper service
- Kafka broker and its service
- Schema registry and its service
- Kafka connect components and its service
Here we go : 
1. Zookeeper installation

```
kubectl apply -f zookeeper.yaml
kubectl apply -f zookeeper-service.yaml
```
2. Kafka-broker installation
```
kubectl apply -f kafka-broker.yaml
kubectl apply -f kafka-service.yaml
```
3. Schema registry installation
```
kubectl apply -f schema-registry.yaml
kubectl apply -f schema-registry-svc.yaml
```
4. Kafka connect installation
```
kubectl apply -f kafka-producer.yaml
kubectl apply -f kafka-producer-svc.yaml
kubectl apply -f kafka-consumer.yaml
kubectl apply -f kafka-consumer-svc.yaml
```
We need to ensure that all pods and services are up and running. Let's check. 
```
kubectl get pod
kubectl get service
```
If you observe something wrong like pod status is in 'RESTARTING | FAILED' or something else, you will need to investigate the root cause. 
```
kubectl logs <pod_name>
kubectl get events
kubectl describe <resource>
```
2. 
