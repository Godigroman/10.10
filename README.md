# Домашнее задание к занятию "`Защита хоста`" - `Клименко Олег`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1

1. Установите eCryptfs.
2. Добавьте пользователя cryptouser.
3. Зашифруйте домашний каталог пользователя с помощью eCryptfs.

`В качестве ответа пришлите снимки экрана домашнего каталога пользователя с исходными и зашифрованными данными.`

![](https://cdn.discordapp.com/attachments/1265236160347766907/1278327275359834206/image.png?ex=66d0668c&is=66cf150c&hm=5d11161b68ac16001dfc380d8079e3baea9242dd85c354599164ffef9163cf50&)

---

### Задание 2

1. Установите поддержку LUKS.
2. Создайте небольшой раздел, например, 100 Мб.
3. Зашифруйте созданный раздел с помощью LUKS.

`В качестве ответа пришлите снимки экрана с поэтапным выполнением задания.`

```
sudo cryptsetup -y -v LuksFormat /dev/sdb
```

![](https://cdn.discordapp.com/attachments/1265236160347766907/1278684960269668384/image.png?ex=66d1b3ab&is=66d0622b&hm=917dc881169851ce047ae741e76db4c0fbabba9a4ae6e79e800a036aa5fb5cec&)

```
sudo cryptsetup LuksOpen /dev/sdb disk
```

![](https://cdn.discordapp.com/attachments/1265236160347766907/1278685449447018647/image.png?ex=66d1b41f&is=66d0629f&hm=e45b9e5f3feec77e9df142c515f24ac3a5fae7974d97e9588becf72730b511df&)

```
la /dev/mapper/disk
```

![](https://cdn.discordapp.com/attachments/1265236160347766907/1278685925844586598/image.png?ex=66d1b491&is=66d06311&hm=116abd1733d047d210bf7831ba72af32216608ddbe937e8fba9893a7d794c37e&)

```
sudo dd if=/dev/zero of=/dev/mapper/disk
```

![](https://cdn.discordapp.com/attachments/1265236160347766907/1278686536677720064/image.png?ex=66d1b523&is=66d063a3&hm=346a8f20a5984844613924d0fc7617ec2a5a560382901b844968f9588f229bf9&)

```
sudo mkfs.ext4 /dev/mapper/disk
```

![](https://cdn.discordapp.com/attachments/1265236160347766907/1278687413371142164/image.png?ex=66d1b5f4&is=66d06474&hm=25963d03586e29608864c712bbec574f4886c6a103a4b22ca20bb23c69f03ba0&)

```
mkdir .secret
sudo mount /dev/mapper/disk .secret/
```

![](https://cdn.discordapp.com/attachments/1265236160347766907/1278329377146273892/image.png?ex=66d06881&is=66cf1701&hm=4db688efe594523514427af2260d4ee1491e72b6caa0bc9aaf349e9eb08ab02e&)

```
ls.secret/
sudo umount .secret
sudo cryptsetup LuksClose disk
ls .secret/
```

![](https://cdn.discordapp.com/attachments/1265236160347766907/1278329566863298600/image.png?ex=66d068ae&is=66cf172e&hm=0333e131ad219a79973c67f415ebf18c6815a635757657b293b8f4f7d17423ab&)

---
---





























