E:\Projects\DevOps\e2e-devops-k8s-microservices-pipleline> minikube start
E:\Projects\DevOps\e2e-devops-k8s-microservices-pipleline> minikube addons enable ingress
# add the text to KUBE_CONFIG_DATA in the actions secert
PS E:\Projects\DevOps\e2e-devops-k8s-microservices-pipleline> [Convert]::ToBase64String([IO.File]::ReadAllBytes("$env:USERPROFILE\.kube\config"))

E:\Projects\DevOps\runners\actions-runner> ./run.cmd

E:\Projects\DevOps\e2e-devops-k8s-microservices-pipleline> git add .
E:\Projects\DevOps\e2e-devops-k8s-microservices-pipleline> git commit -m "final commit"
E:\Projects\DevOps\e2e-devops-k8s-microservices-pipleline> git push -u origin main

E:\Projects\DevOps\e2e-devops-k8s-microservices-pipleline> minikube tunnel


http://reactjs.local/
http://api.local/
