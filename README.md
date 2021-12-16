# Задача 1: Рассмотрите пример 14.5/example-security-context.yml

Применим ямл с конфигурацией:
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: security-context-demo
spec:
  containers:
  - name: sec-ctx-demo
    image: fedora:latest
    command: [ "id" ]
    securityContext:
      runAsUser: 1100
      runAsGroup: 3000
```

и убедимся что настройки видны:
```shell
desema@control1:~$ kubectl logs security-context-demo
uid=1100 gid=3000 groups=3000
```