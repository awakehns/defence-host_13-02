# Домашнее задание к занятию "`Защита хоста`" - `Демин Герман`

### Задание 1

Установка eCryptfs, создание пользователя cryptouser, шифрование домашнего каталога:

```
sudo dnf update

sudo dnf install ecryptfs -y

sudo adduser cryptouser

sudo passwd cryptouser 

su - cryptouser

exit

authselect current

sudo authselect enable-feature with-ecryptfs

sudo authselect apply-changes

sudo usermod -aG ecryptfs cryptouser

sudo ecryptfs-migrate-home -u cryptouser
```

Установка завершена:
![ecryptfs-install](/img/ecryptfs-install.png)

Пользователь создан:
![cryptouser-created](/img/cryptouser-created.png)

Домашний каталог до шифрования:
![base-home](/img/base-home.png)

Шифрование домашнего каталога:
![encrypt-home](/img/encrypt-home.png)

![encrypt-home-2](/img/encrypt-home-2.png)

Домашний каталог зашифрован:
![encrypted-home](/img/encrypted-home.png)

### Задание 2

