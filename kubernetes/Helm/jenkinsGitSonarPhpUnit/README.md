WORK IN PROGRESS

# jenkinsGitSonarPhpUnit
Usar todas estas tecnologías juntas en kubernetes

TRAEFIK:
```
  helm fetch stable/traefik
  helm install --name traefik -f values.yaml --namespace kube-system stable/traefik
  tar xf traefik-1.78.4.tgz
  cd traefik
  //DESPLEGAMOS
  helm install --name traefik -f values.yaml stable/traefik
```
JENKINS:
```
  helm fetch stable/jenkins
  tar xf jenkins-1.7.8.tgz
  cd jenkins
  //descubrimos el servicio jenkins
vi values.yaml
```
```...
service:
  type: LoadBalancer
  
....

ingress:
...
  annotations:
    kubernets.io/ingress.class: traefik
...
```

DESPLEGAMOS JENKINS
```
  helm install --name jenkins -f values.yaml stable/jenkins
```

SONARQUBE:
```
  helm fetch stable/sonarqube
  tar xf sonarqube-3.2.0.tgz
  cd sonarqube
```
  //descubrimos el servicio sonarqube
vi values.yaml
```
...
service:
  type: LoadBalancer
  
....

ingress:
...
  annotations:
    kubernets.io/ingress.class: traefik
...
```
```
helm install --name sonarqube -f values.yaml stable/sonarqube
```
```
//exportamos la variable
export SERVICE_IP_SONAR=$(kubectl get svc --namespace default sonarqube-sonarqube -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
//el puerto por defecto 9000 de helm 
//Obtener acceso:
echo http://$SERVICE_IP_SONAR:9000
```
Usuario por defecto
```
username: admin
pass: admin
```

