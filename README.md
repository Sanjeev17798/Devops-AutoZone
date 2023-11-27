# Devops-AutoZone

apiVersion: apps/v1
kind: Deployment
metadata:
  name: AutoZone-app-deployment
  labels:
    app: Autozone-app
spec:
  replicas: 3  # high availability
  selector:
    matchLabels:
      app: AutoZone-app
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1
      maxUnavailable: 1
  template:
    metadata:
      labels:
        app: AutoZone-app
    spec:
      containers:
      - name: AutoZone-app
        image: nginx  # using nginx as a image 
        ports:
        - containerPort: 80
