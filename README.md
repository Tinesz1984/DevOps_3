# Лабораторная работа №3
# Часть 1

Задча: настроить nginx с https сертификатом, принудительно перенаправлять запросы с http на https, использовать alias и настроить виртуальные хосты. 

В ходе работы были выполнены слежующие шаги: 
1. Установлен ngnix (`brew install nginx`)
2. Создана структура проекта
   
<img width="320" height="406" alt="image" src="https://github.com/user-attachments/assets/486089af-bb84-4111-af5b-9caede88999a" />

3. Добавлены локальные домены

<img width="965" height="463" alt="image" src="https://github.com/user-attachments/assets/cfbac8a4-f500-4e45-b24f-55adf2f8b947" />

4. Установлен  **mkcert** для локальных HTTPS-сертификатов. **mkcert** создает локально доверенные сертификаты.

5. Созданы конфиги сайтов:

Использован alias:

```
location /files/ {
    alias /Users/arina/nginx-lab/pet1/assets/;
    autoindex on;
}
```

Настроены виртуальные хосты:

```
server {
    listen 80;
    server_name pet1.local;
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl;
    server_name pet1.local;
    ...
}
```

Итого: 

<img width="464" height="242" alt="image" src="https://github.com/user-attachments/assets/64dc7f24-65b0-4ca7-8661-8d66ce8f25a5" />

<img width="338" height="262" alt="image" src="https://github.com/user-attachments/assets/541cdf33-e7c9-4b59-8e52-0fb41dc88359" />


