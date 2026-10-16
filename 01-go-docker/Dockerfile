# Сборка проекта
FROM golang:1.27 AS builder
# Задаем рабочую директорию 
WORKDIR /app
# Копируем в сборку файл с кодом
COPY main.go .
# Отключаем поддержку С для GO тк в дальнейшем используем scratch пустой без библиотек, указываем систему для GO-приложения, комилируем приложение. 
RUN CGO_ENABLED=0 GOOS=linux go build -o server main.go
# Пересборка проекта на минимальный образ
FROM scratch
# Копируем приложение из предыдущего образа
COPY --from=builder /app/server /server
# Декларируем порт для приложения  
EXPOSE 8080
# Запускаем наш бинарник
ENTRYPOINT [ "/server" ]