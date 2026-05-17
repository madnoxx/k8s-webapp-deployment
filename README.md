# Ghost Blog Helm Deployment

Этот проект демонстрирует подход Infrastructure as Code (IaC) для развертывания многокомпонентного веб-приложения в Kubernetes.

## Архитектура

- Приложение: Ghost (Node.js) + MariaDB (через Helm subchart dependency).
- Настройки вынесены в values.yaml. Передача чувствительных данных (паролей) реализована через Kubernetes Secrets (интеграция с секретами Bitnami MariaDB).
- Доступ извне настроен через Ingress (L7 маршрутизация).
- В проекте настроен GitHub Actions пайплайн, который при каждом коммите выполняет загрузку зависимостей, проверку синтаксиса (helm lint) и тестовый рендеринг манифестов (helm template).

## Запуск локально

1. helm dependency update ./ghost-blog
2. helm install ghost-release ./ghost-blog
3. Добавьте 127.0.0.1 my-ghost-blog.local в файл /etc/hosts и откройте браузер.


