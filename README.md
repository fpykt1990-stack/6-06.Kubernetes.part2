# Домашнее задание к занятию «Kubernetes. Часть 2»

Это задание для самостоятельной отработки навыков и не предполагает обратной связи от преподавателя. Его выполнение не влияет на завершение модуля. Но мы рекомендуем его выполнить, чтобы закрепить полученные знания.

**Задание 1**

Выполните действия:

Создайте свой кластер с помощью kubeadm.
Установите любой понравившийся CNI плагин.
Добейтесь стабильной работы кластера.

**Ответ 1**

Был установлен runtime— containerd, CNI — Flannel. Отключен swap. Установлен br_netfilter для запуска Flannel. 

![Ответ4](https://github.com/fpykt1990-stack/6-06.Kubernetes.part2/blob/main/img/img-kub-10.png)

![Ответ4](https://github.com/fpykt1990-stack/6-06.Kubernetes.part2/blob/main/img/img-kub-11.png)

**Задание 2**

Есть файл с деплоем:


---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: redis
spec:
  selector:
    matchLabels:
      app: redis
  replicas: 1
  template:
    metadata:
      labels:
        app: redis
    spec:
      containers:
      - name: master
        image: bitnami/redis
        env:
         - name: REDIS_PASSWORD
           value: password123
        ports:
        - containerPort: 6379
Выполните действия:

Создайте Helm Charts.
Добавьте в него сервис.
Вынесите все нужные, на ваш взгляд, параметры в values.yaml.
Запустите чарт в своём кластере и добейтесь его стабильной работы.

**Задание 3**
Изучите документацию по подключению volume типа hostPath.
Дополните деплоймент в чарте подключением этого volume.
Запишите что-нибудь в файл на сервере, подключившись к поду с помощью kubectl exec, и проверьте правильность подключения volume.