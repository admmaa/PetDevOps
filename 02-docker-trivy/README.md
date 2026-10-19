##Цель

Анализ безопасности docker-образа с использованием Trivy и Syft.

##Инструменты

Docker - создание образа, Trivy - сканирует безопасность, Syft - получаем список компонентов в образе.

##Запуск

Скачайте проект и перейдите в него. Соберите образ  "docker build -t pet02-security ." 
Установите Trivy и Syft 
Проверить образ "trivy image --severity HIGH,CRITICAL pet02-security"
Проверить конфигурацию Dockerfile "trivy config .".
Создание SBOM(инвентаризация всех компонентов образа) "syft pet02-security -o cyclonedx-json=reports/sbom.cdx.json" (используется в мониторингах, для ci/cd)
