# raspberry

### Baixe a imagem do ubuntu server para o seu raspberry
https://ubuntu.com/download/raspberry-pi

Conecte o raspberry via ssh
```console
ssh ubuntu@ubuntu
```

Troque o hostname
```console
sudo hostnamectl set-hostname cluster-node-1
```

Reinicie
```console
sudo reboot
```

Reconecte via ssh
```console
ssh ubuntu@cluster-node-1 
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
