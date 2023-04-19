# Лабораторная работа №3

### Цели и задачи:
1. Ознакомиться с основными понятиями `Kubernates`.
2. Получить практические навыки работы с утилитой `kubectl`.
3. Реализовать манифесты для разворачивания своих сервисов в кластере `Kubernates`.

### Шаги выполнения лабораторной работы

#### 1. Настройка тестовой среды разработки.

Для разворачивания Single-Nodes кластера Kubernates достаточно в приложении Docker Desktop поставить галочку 
- **Settings->Kubernates->Enable Kubernates**
- Для удобного использования утилиты `kubectl` на `Windows` можно добавить полный путь в переменные среды **PATH**: https://docs.docker.com/desktop/kubernetes/

Если вы используете Docker без приложения Docker Desktop, эмулировать работу с кластером можно с помощью `minikube`. Подробную инструкцию по установки можно найти на официальном сайте: https://kubernetes.io/ru/docs/tasks/tools/install-minikube/

Для проверки работоспособности выполнить команду:

`kubectl get nodes`

#### 2. Создание Pods.

1. Проверить список подов. `kubectl get pods`

2. Запустить под. `kubectl run <pod-name> --image=nginx:latest --port 80`

3. Посмотреть подробное описание пода. `kubectl describe pods <pod-name>`

4. Прокинуть порт. `kubectl port-forward <pod-name> 8080:80`

5. Попробовать достучаться до пода через браузер.

6. Удалить под. `kubectl delete pods <pod-name>`

7. Изучить файл с манифестом для создания подов.

8. Создание пода с помощью файла манифеста. `kubectl apply -f <pod-manifest-file-name>.yaml`

9. Удаление пода с помощью файла манифеста. `kubectl delete -f <pod-manifest-file-name>.yaml`

#### 2. Создание Deployment.

1. Проверить список деплойментов. `kubectl get deployments`

2. Создать деплоймент. `kubectl create deployment <deployment-name> --image nginx:latest`

3. Проверьте список созданных подов и деплойментов.

4. Посмотреть подробное описание деплоймента. `kubectl describe deployments <deployment-name>`

5. Создать несколько одинаковых экземпляров подов. `kubectl scale deployments <deployment-name> --replicas 4`

6. Проверьте список созданных подов и деплойментов.

7. Проверьте список ReplicaSet. `kubectl get rs`

8. Попробуйте удалить один из подов и смотрите что будет происходить со списоком подов.

9. Удалите деплоймент. `kubectl delete deployments <deployment-name>`

10. Создайте новый деплоймент, но для маштабирования используйте AutoScaling. `kubectl autoscale deployment <deployment-name> --min 2 --max 5 --cpu-percent=80`

11. Посмотреть список автоматического горизонтального масштабирования подов. `kubectl get hpa`

12. Удалите Deployment и AutoScaling. `kubectl delete hpa <deployment-name>`

13. Изучить файл с манифестом для создания деплойментов.

14. Создать деплоймент с помощью файла манифеста. `kubectl apply -f <deployment-manifest-file-name>.yaml`

15. Удаление деплоймент с помощью файла манифеста. `kubectl delete -f <deployment-manifest-file-name>.yaml`

#### Создание Service.

