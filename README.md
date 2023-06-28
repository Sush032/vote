Architecture

![image](https://github.com/Sush032/vote/assets/86153084/0bc70cea-85c3-447f-a190-c5f86273b016)

A front-end web app in Python which lets you vote between two options
A Redis which collects new votes
A .NET worker which consumes votes and stores them in db
A Postgres database backed by a Docker volume
A Node.js web app which shows the results of the voting in real time

1. Written a jenkins pipeline inside vote repo. which consists of several stages like first pick the code from github,build,test,push the image into ECR and last it will update the tag written in the vote deployment.
2. Second jenkins file written in kube repo. it will pick the latest tag and with the help of Argocd it will get deployed in kubernetes cluster.
3.Argocd is deployed on kubernetes cluter with the help of Helm.
4. With the help of Terrafrom created a kubernetes cluster.
5. Also Setup ingress with the help of terraform.






![image](https://github.com/Sush032/vote/assets/86153084/c38c32a0-030a-4f6d-9f1b-102630450008)

![image](https://github.com/Sush032/vote/assets/86153084/744a6a2e-96fb-4e09-917a-8de69208148c)
