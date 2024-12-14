# Домашнее задание к занятию "Что такое DevOps. CI/CD" - Еноктаев Олег



---
### Задание 1.
 1. Установите себе jenkins по инструкции из лекции или любым другим способом из официальной документации. Использовать Docker в этом задании нежелательно.
 2. Установите на машину с jenkins golang.
 3. Используя свой аккаунт на GitHub, сделайте себе форк репозитория. В этом же репозитории находится дополнительный материал для выполнения ДЗ.
 4. Создайте в jenkins Freestyle Project, подключите получившийся репозиторий к нему и произведите запуск тестов и сборку проекта go test . и docker build ..
###### В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.



  1. Сначала устанавливаем Java: 
  ```
  sudo apt-get install default-jre
  ```
 Для установки jenkins 
 ```
 curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key |
sudo tee \
/usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null`
sudo apt-get update
sudo apt-get install jenkins
```
![JENKINS](https://github.com/incid3nt/devops_jenkins/blob/main/Code_imOhg6d3gb.png?raw=true)

2. Установка golang
```
wget https://go.dev/dl/go1.17.5.linux-amd64.tar.gz
rm -rf /usr/local/go && tar -C /usr/local -xzf go1.17.5.linux-amd64.tar.gz
echo 'export PATH=$PATH:/usr/local/go/bin' >> /etc/profile
```
3. Сделал форк репоизтория
![FORK](https://github.com/incid3nt/devops_jenkins/blob/main/chrome_URGoREiMAc.png)
4. Все получилось:
![step](https://github.com/incid3nt/devops_jenkins/blob/main/step.png)
![ok](https://github.com/incid3nt/devops_jenkins/blob/main/ok.png)
![success](https://github.com/incid3nt/devops_jenkins/blob/main/success.png)

###### А еще важное в nexus нужно добавить репозиторий и добавить порт.
![nexus](https://github.com/incid3nt/devops_jenkins/blob/main/chrome_qIrgBFM9rg.png)
![nexus](https://github.com/incid3nt/devops_jenkins/blob/main/chrome_bDkLhdELCw.png)

###### а так же внести изменения в /etc/hosts
```
127.0.0.1	localhost
127.0.1.1	devops

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
192.168.1.10 ubuntu-bionic
```
---

### Задание 2

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота 2](ссылка на скриншот 2)`


---

### Задание 3

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`

### Задание 4

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`
