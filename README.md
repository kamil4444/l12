# Stworzono repozytorium prywatne na dockerhubie, secret i poda.
kubectl create secret generic regcred --from-file=.dockerconfigjson=/home/kamil/.docker/config.json --type=kubernetes.io/dockerconfigjson
![gh1](https://github.com/kamil4444/l12/assets/103449118/2fdf6496-9c6f-4545-9d39-12fae55df997)

![gh2](https://github.com/kamil4444/l12/assets/103449118/a27a1501-7c26-4d81-8a55-cc1cc87bad5c)

![gh3](https://github.com/kamil4444/l12/assets/103449118/b1586c95-f8ad-4a61-ae88-cd5caa8fd6cc)
