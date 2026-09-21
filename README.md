# Lab Kubernetes - Flask

Laboratorio de escalado de una aplicación Flask utilizando Kubernetes.

## Componentes

- Flask + Gunicorn
- Kubernetes Deployment
- Kubernetes Service
- Escalado manual de Pods
- Balanceo de carga
- Self-healing
- Horizontal Pod Autoscaler (HPA)
- Metrics Server

## Estructura

flask-k8s-app/
+-- app/
¦   +-- app.py
¦   +-- requirements.txt
¦   +-- Dockerfile
+-- k8s/
¦   +-- 01-deployment.yaml
¦   +-- 02-service.yaml
+-- scripts/
    +-- balanceo.sh

## Ejecución

Construir la imagen:

    docker build -t flask-k8s-app:1.0 ./app

Aplicar Deployment y Service:

    kubectl apply -f k8s/01-deployment.yaml
    kubectl apply -f k8s/02-service.yaml

Verificar:

    kubectl get pods
    kubectl get deployment flask-app
    kubectl get svc flask-service

## HPA

Metrics Server permite observar el consumo de recursos:

    kubectl top pods

Verificar el HPA:

    kubectl get hpa
