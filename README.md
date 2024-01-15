HELM - Very simple exercise create nginx chart 

note:   
inspired by :   
https://devopscube.com/create-helm-chart/ . 
https://www.youtube.com/watch?v=DQk8HOVlumI&t=3188s   
but i removed all dir and files from scratch and used customs values  
dir test is helping you to verify issues 

TEST 1   
create a nginx chart 
either with create or create directories by yourself  
Adding default values for the pod 
If you using the yaml below, you will get errors that we gonna fix later  
metadata values 
spec container values 
lint the helm chart 
usually you don't stand in the helmchart directory 
template and verify the output  
usually you don't stand in the helmchart directory 
install with dry-run and verify the output 
usually you don't stand in the helmchart directory  
test debug flag 
Change any error you getting
and why you getting this error
install the pod with the helm chart
If not the pod is created successful  fix the issues
Verify that the pod is created and with your values



```yaml

MY STRUCTURE:
> tree -l
.
├── Chart.yaml
├── templates
│   └── helm-pod-template.yaml
└── values.yaml

2 directories, 3 files

```


```yaml

helm-pod-template.yaml:
apiVersion: v1
kind: pod
metadata:
  name: {{ .Values.name }} 
spec:
  containers:
  - name: {{ .Values.container.name }}
    image: {{ .Values.container.image }}
    port: {{ .Values.container.port }}
        
Chart.yaml
apiVersion: v2
name: nginx-chart
description: My First Helm Chart
type: application
version: 0.1.0
appVersion: "1.0.0"
maintainers:
- email: contact@misk.com
  name: devopscube

```

```yaml

values.yaml
name: misk-app
container:
  name : misk-app-container
  image: my-app-image
  port: 9001
```





command to use:  
> helm lint ./nginx-chart   
> helm template ./nginx-chart  
> helm install mynginx-custom-realease  ./nginx-chart --dry-run  
