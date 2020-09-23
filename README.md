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
