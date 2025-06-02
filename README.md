# kubectl-kubeplugin

Плагін для kubectl для отримання статистики використання ресурсів у Kubernetes кластері.

## Встановлення

1. Завантажте скрипт і зробіть його виконуваним:
```bash
wget https://raw.githubusercontent.com/[username]/[repo]/main/scripts/kubeplugin
chmod +x kubeplugin
```

2. Встановіть як kubectl плагін:
```bash
sudo cp kubeplugin /usr/local/bin/kubectl-kubeplugin
```

3. Перевірте встановлення:
```bash
kubectl plugin list
```

## Використання

### Синтаксис
```bash
kubectl kubeplugin <resource_type> <namespace>
```

### Приклади
```bash
# Отримати статистику подів у namespace kube-system
kubectl kubeplugin pod kube-system

# Отримати статистику подів у namespace default  
kubectl kubeplugin pod default
```

## Формат виводу

```
Resource, Namespace, Name, CPU, Memory
pod, kube-system, coredns-ff8999cc5-gdcx5, 6m, 17Mi
pod, kube-system, metrics-server-6f4c6675d5-77pjx, 8m, 24Mi
```

## Вимоги

- kubectl встановлений і налаштований
- metrics-server працює у кластері
- Доступ до цільового namespace

## Приклад реального виводу

```
Resource, Namespace, Name, CPU, Memory
pod, kube-system, coredns-ff8999cc5-gdcx5, 6m, 17Mi
pod, kube-system, local-path-provisioner-774c6665dc-flf66, 1m, 12Mi
pod, kube-system, metrics-server-6f4c6675d5-77pjx, 8m, 24Mi
pod, kube-system, svclb-traefik-00f026b7-kx46x, 0m, 0Mi
pod, kube-system, traefik-67bfb46dcb-ppf6t, 2m, 30Mi
```