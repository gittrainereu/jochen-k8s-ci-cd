apiVersion: apps/v1
kind: Deployment
metadata:
  name: echo-server-deployment
  labels:
    app: echo-server
spec:
  selector: 
    matchLabels:  
      app: echo-server 
  replicas: 1
  template:
    metadata:
      annotations:
      labels:
        app: echo-server
    spec:
      containers:
        - name: echo-server
          image: hashicorp/http-echo
          imagePullPolicy: IfNotPresent
          args:
            - -listen=:8080
            - -text="hello world"
