# Домашнее задание к занятию "Что такое DevOps. CI/CD" - Еноктаев Олег



---
### Задание 1.
 1. Установите себе jenkins по инструкции из лекции или любым другим способом из официальной документации. Использовать Docker в этом задании нежелательно.
 2. Установите на машину с jenkins golang.
 3. Используя свой аккаунт на GitHub, сделайте себе форк репозитория. В этом же репозитории находится дополнительный материал для выполнения ДЗ.
 4. Создайте в jenkins Freestyle Project, подключите получившийся репозиторий к нему и произведите запуск тестов и сборку проекта go test . и docker build ..
###### В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

---

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
![JENKINS](https://github.com/incid3nt/devops_jenkins/blob/main/screenshots/Code_imOhg6d3gb.png?raw=true)

2. Установка golang
```
wget https://go.dev/dl/go1.17.5.linux-amd64.tar.gz
rm -rf /usr/local/go && tar -C /usr/local -xzf go1.17.5.linux-amd64.tar.gz
echo 'export PATH=$PATH:/usr/local/go/bin' >> /etc/profile
```
3. Сделал форк репоизтория
![FORK](https://github.com/incid3nt/devops_jenkins/blob/main/screenshots/chrome_URGoREiMAc.png)
4. Все получилось:
![step](https://github.com/incid3nt/devops_jenkins/blob/main/screenshots/step.png)
![ok](https://github.com/incid3nt/devops_jenkins/blob/main/screenshots/ok.png)
![success](https://github.com/incid3nt/devops_jenkins/blob/main/screenshots/success.png)

###### А еще важное в nexus нужно добавить репозиторий и добавить порт.
![nexus](https://github.com/incid3nt/devops_jenkins/blob/main/screenshots/chrome_qIrgBFM9rg.png)
![nexus](https://github.com/incid3nt/devops_jenkins/blob/main/screenshots/chrome_bDkLhdELCw.png)

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
###### создать файл в /etc/docker/daemon.json 
```
{
      "insecure-registries" : ["ubuntu-bionic:8082"]
}
```
---

### Задание 2.
 1. Создайте новый проект pipeline.
 2. Перепишите сборку из задания 1 на declarative в виде кода.

---
1. Здесь скриншот:
![pipeline](https://github.com/incid3nt/devops_jenkins/blob/main/screenshots/chrome_XiI5sGAUBH.png)
2. А это код пайплайна
```
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/netology-code/sdvps-materials.git'
            }
        }

        stage('Test') {
            steps {
                sh '/usr/local/go/bin/go test .'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    def buildNumber = env.BUILD_NUMBER ?: "1"
                    sh "docker build . -t ubuntu-bionic:8082/hello-world:v${buildNumber}"
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                
                    sh """
                        docker login -u admin -p admin ubuntu-bionic:8082
                        docker push ubuntu-bionic:8082/hello-world:v${env.BUILD_NUMBER}
                        docker logout
                    """
                }
            }
        }
    }

```
---
### Задание 3.
 1. Установите на машину Nexus.
 2. Создайте raw-hosted репозиторий.
 3. Измените pipeline так, чтобы вместо Docker-образа собирался бинарный go-файл. Команду можно скопировать из Dockerfile.
 4. Загрузите файл в репозиторий с помощью jenkins.
 ---

1. Установил nexus.
![nexus](https://github.com/incid3nt/devops_jenkins/blob/main/screenshots/Code_IQWPqkonFS.png)
2. Создал raw-hosted репозиторий.
![nexus](https://github.com/incid3nt/devops_jenkins/blob/main/screenshots/chrome_RNBJOOUL0d.png)