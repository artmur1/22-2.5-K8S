# Домашнее задание к занятию «Helm»

### Цель задания

В тестовой среде Kubernetes необходимо установить и обновить приложения с помощью Helm.

------

### Чеклист готовности к домашнему заданию

1. Установленное k8s-решение, например, MicroK8S.
2. Установленный локальный kubectl.
3. Установленный локальный Helm.
4. Редактор YAML-файлов с подключенным репозиторием GitHub.

------

### Инструменты и дополнительные материалы, которые пригодятся для выполнения задания

1. [Инструкция](https://helm.sh/docs/intro/install/) по установке Helm. [Helm completion](https://helm.sh/docs/helm/helm_completion/).

------

### Задание 1. Подготовить Helm-чарт для приложения

1. Необходимо упаковать приложение в чарт для деплоя в разные окружения. 
2. Каждый компонент приложения деплоится отдельным deployment’ом или statefulset’ом.
3. В переменных чарта измените образ приложения для изменения версии.

### Решение 1

Создал чарт murchin-chart, и внес правки:

    helm create murchin-chart

https://github.com/artmur1/22-2.5-K8S/blob/main/files/murchin-chart/Chart.yaml

![](https://github.com/artmur1/22-2.5-K8S/blob/main/img/22-2_5-01-01.png)

deployment.yaml для nginx:

https://github.com/artmur1/22-2.5-K8S/blob/main/files/murchin-chart/templates/deployment.yaml

![](https://github.com/artmur1/22-2.5-K8S/blob/main/img/22-2_5-01-03.png)

Прописал переменные:

https://github.com/artmur1/22-2.5-K8S/blob/main/files/murchin-chart/values.yaml

![](https://github.com/artmur1/22-2.5-K8S/blob/main/img/22-2_5-01-02.png)

service.yaml:

https://github.com/artmur1/22-2.5-K8S/blob/main/files/murchin-chart/templates/service.yaml

![](https://github.com/artmur1/22-2.5-K8S/blob/main/img/22-2_5-01-04.png)

Прописал переменные values2.yaml с другой версией nginx:

https://github.com/artmur1/22-2.5-K8S/blob/main/files/values2.yaml

![](https://github.com/artmur1/22-2.5-K8S/blob/main/img/22-2_5-01-05.png)

Прописал переменные values3.yaml с версией nginx: latest:

https://github.com/artmur1/22-2.5-K8S/blob/main/files/values3.yaml

![](https://github.com/artmur1/22-2.5-K8S/blob/main/img/22-2_5-01-06.png)

------
### Задание 2. Запустить две версии в разных неймспейсах

1. Подготовив чарт, необходимо его проверить. Запуститe несколько копий приложения.
2. Одну версию в namespace=app1, вторую версию в том же неймспейсе, третью версию в namespace=app2.
3. Продемонстрируйте результат.

### Решение 2

Чарт прошел успешное тестирование:

![](https://github.com/artmur1/22-2.5-K8S/blob/main/img/22-2_5-02-01.png)

Запустил одну версию в namespace=app1, вторую версию в том же неймспейсе, третью версию в namespace=app2:

![](https://github.com/artmur1/22-2.5-K8S/blob/main/img/22-2_5-02-02.png)

Видно, что все helm charts стартовали:

![](https://github.com/artmur1/22-2.5-K8S/blob/main/img/22-2_5-02-03.png)

Также работают деплойменты и поды:

![](https://github.com/artmur1/22-2.5-K8S/blob/main/img/22-2_5-02-04.png)

### Правила приёма работы

1. Домашняя работа оформляется в своём Git репозитории в файле README.md. Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.
2. Файл README.md должен содержать скриншоты вывода необходимых команд `kubectl`, `helm`, а также скриншоты результатов.
3. Репозиторий должен содержать тексты манифестов или ссылки на них в файле README.md.

