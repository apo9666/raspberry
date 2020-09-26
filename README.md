# raspberry

### Baixe a imagem do ubuntu server para o seu raspberry
https://ubuntu.com/download/raspberry-pi

Conecte o raspberry via ssh
```console
ssh ubuntu@ubuntu
senha ubuntu
```
Caso receba esse aviso "WARNING: POSSIBLE DNS SPOOFING DETECTED!" execute:
```console
ssh-keygen -R ubuntu
```

Troque o hostname
```console
sudo hostnamectl set-hostname cluster-master
```

Reinicie
```console
sudo reboot
```

Reconecte via ssh
```console
ssh ubuntu@cluster-master
```

Atualize o sistema
```console
sudo apt update
sudo apt upgrade
sudo reboot
```

Habilite o cgroup editando o arquivo
```console
sudo nano /boot/firmware/cmdline.txt
```
adicione ao final
```
cgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1
```


Instale o kubernetes
```console
sudo snap install microk8s --classic
sudo microk8s start
sudo microk8s status
```

Instale o dashboard
```console
sudo microk8s enable dashboard
token=$(sudo microk8s kubectl -n kube-system get secret | grep default-token | cut -d " " -f1)
sudo microk8s kubectl -n kube-system describe secret $token
sudo microk8s kubectl port-forward -n kube-system service/kubernetes-dashboard 10443:443 --adess 0.0.0.0
```

Acesse a dashboard
https://cluster-master:10443

Adicionando nós ao cluster
```console
sudo microk8s.add-node
```


