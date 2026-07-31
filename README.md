Після підключення до bastion-сервера перевірити доступність Kubernetes API:
kubectl cluster-info

Перевірити доступні ноди: kubectl get nodes
Перевірити стан системних компонентів: kubectl get pods -n kube-system

Після перевірки роботи кластера можемо розпочати зі створення Namespace для свого застосунку

Для Podinfo: kubectl create namespace podinfo

Перевірка: kubectl get ns

Створимо Deployment:
nano deployment.yaml # код беремо з поточного репозиторію

Запускаємо: kubectl apply -f deployment.yaml
Перевірка: kubectl get deployment -n podinfo

Перевірка, що застосунок розподілився між всіма воркерами:
kubectl get pods -n podinfo -o wide

Створення Service
nano service.yaml # код беремо з поточного репозиторію

Запускаємо: kubectl apply -f service.yaml
Перевірка: kubectl get svc -n podinfo

Створення Ingress
nano ingress.yaml # код беремо з поточного репозиторію

Запускаємо: kubectl apply -f ingress.yaml
Перевірка: kubectl get ingress -n podinfo

На рівні віртуалізації має бути відкриті 2 порти 443 та 80 і після цього доступ буде зовні по https://zoltraak.pp.ua
Але без ссл сертифікату.
