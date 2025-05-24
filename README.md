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

Установка поддержки LUKS, создание и шифрование небольшого раздела:

```
sudo dnf install cryptsetup -y

dd if=/dev/zero of=/var/tmp/secure_container.img bs=1M count=100

sudo cryptsetup luksFormat /var/tmp/secure_container.img

sudo cryptsetup open /var/tmp/secure_container.img secure_volume

sudo mkfs.ext4 /dev/mapper/secure_volume

sudo mkdir /mnt/secure

sudo mount /dev/mapper/secure_volume /mnt/secure

sudo umount /mnt/secure

sudo cryptsetup close secure_volume
```

Установлена поддержка LUKS, создан раздел на 100мб:
![install-LUKS-and-create-img](/img/install-LUKS-and-create-img.png)

Зашифрован раздел:
![create-secure-tom](/img/create-secure-tom.png)

Смонтирован и размонтирован зашифрованный раздел:
![mount-tom](/img/mount-tom.png)

Открытый раздел:
![tom-enter](/img/tom-enter.png)












