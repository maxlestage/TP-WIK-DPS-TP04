# TP-WIK-DPS-TP04

## CONSIGNES

Pour chaque étape il faut produire les fichiers YAML nécessaires et les conserver pour les communiquer lors du rendu.

- Créer un Pod pour déployer l'image registry.cluster.wik.cloud/public/echo (c'est l'image créée lors du TP WIK-DPS-TP02) et le tester sur minikube en local.

- Pour le tester vous devez faire un port-forwarding entre le port du Pod sur lequel votre API écoute et un port sur votre hôte.

- Remplacer le Pod par un ReplicaSet afin de déployer 4 réplicas du Pod créé précédemment.

- Remplacer le ReplicaSet par un Deployment afin de pouvoir définir une stratégie d'update en RollingRelease (50% en maxUnavailable).

- Créer un Service pour pouvoir communiquer avec les Pod du ReplicaSet créé précédemment, pour le tester vous devez faire un port-forwarding entre le port du Service sur lequel votre API écoute et un port sur votre hôte.

- Activer le plugin ingress nginx sur minikube et créer un Ingress (nom de domaine au choix) pour communiquer avec le Service créé précédemment.

- Tester en ajoutant le nom de domaine choisi dans /etc/hosts afin de résoudre localement vers le service nginx de minikube.

- Vous pouvez alors accéder via votre navigateur au service créé précédemment
Faites une capture d'écran de la page sur votre navigateur avec le nom de domaine de votre choix pour votre service.

---

## Les Technos

- Docker
- Kubernetes
- Minikube

---

## Pour tester chaques parties du TP

Commande à lancer dans le temrinal à la racine du projet :

La commande ci-jointe est nécessaire sur Mac M1 afin que tout fonctionne.

```cmd
minikube tunnel
```

### Partie 1

```cmd
 minikube start
```

```cmd
minikube tunnel
```

```cmd
minikube addons enable ingress
```

```cmd
kubectl apply -f pod.yaml
```

```cmd
kubectl get pod
```

```cmd
kubectl port-forward publicecho  8080:8080
```

```cmd
kubectl delete pod publicecho
```

### Partie 2

```cmd
minikube start
```

```cmd
minikube tunnel
```

```cmd
minikube addons enable ingress  
```

```cmd
kubectl apply -f replicaset.yaml
```

```cmd
kubectl get pods 
```

```cmd
kubectl get serviceskubectl port-forward replicaset.apps/part2 8080:8080
```

```cmd
kubectl delete replicaset.apps/part2
```

```cmd
kubectl get services 
```

### Partie 3

```cmd
minikube start
```

```cmd
minikube tunnel
```

```cmd
minikube addons enable ingress  
```

```cmd
kubectl apply -f deployment.yaml
```

```cmd
kubectl  get services
```

```cmd
kubectl port-forward deployment.apps/part3  8080:8080
```

### Partie 4

```cmd
minikube start
```

```cmd
minikube tunnel
```

```cmd
minikube addons enable ingress 
```

```cmd
kubectl apply -f ingress.yaml
```

```cmd
kubectl get pods,services,deployments,ingress.networking.k8s.io 
```

---

## Une capture d'écran de la page sur le navigateur avec le nom de domaine personalisé

![screenshot](https://github.com/maxlestage/TP-WIK-DPS-TP04/blob/main/MicrosoftTeams-image.png)

---

LESTAGE Maxime - TP DevOps n°4 - Ynov 2022.
