### README.md

# Сервер на сокетах для обработки HTTP-запросов

Данный проект представляет собой простой сервер на сокетах, который принимает и обрабатывает HTTP-запросы, такие как GET, POST, PUT, DELETE, TRACE, OPTIONS и HEAD. Сервер реализован на языке C++ с использованием Windows Sockets API (WinSock).

## Функциональность сервера

Сервер работает на IP-адресе `127.0.0.1` и порту `80`, обрабатывая следующие HTTP-запросы:

- **GET**: 
  - `/`: Возвращает содержимое файла `index.html`.
  - `/image`: Возвращает изображение `test.png`.
  - `/site/{путь}`: Возвращает содержимое файла по указанному пути.
  - `/doc`: Возвращает содержимое документа по указанному пути.
- **POST**: Обрабатывает отправленные данные и возвращает сообщение об успешном получении.
- **PUT**: Сохраняет отправленные данные в файл `from PUT.txt` и возвращает сообщение об успешном получении.
- **DELETE**: Удаляет указанный файл и возвращает сообщение об успешном выполнении операции.
- **OPTIONS**: Возвращает список поддерживаемых методов (`GET, HEAD, POST, PUT, DELETE, TRACE`).
- **HEAD**: Возвращает только заголовки HTTP-ответа.
- **TRACE**: Возвращает полученные HTTP-заголовки в теле ответа.

### Структура проекта

- **main.cpp**: Основной файл программы, содержащий логику работы сервера.
- **index.html**: Файл, содержимое которого возвращается при GET-запросе к `/`.
- **test.png**: Изображение, которое возвращается при GET-запросе к `/image`.
- **from PUT.txt**: Файл, в который сохраняются данные, отправленные с помощью PUT-запроса.

### Сборка и запуск

1. **Требования**: 
   - Windows OS
   - Компилятор, поддерживающий C++ (например, Visual Studio)
   - Библиотека WinSock (подключается автоматически через `#pragma comment(lib, "Ws2_32.lib")`)

2. **Сборка проекта**:
   - Откройте проект в IDE (например, Visual Studio).
   - Скомпилируйте проект, убедитесь, что все необходимые файлы (например, `index.html` и `test.png`) находятся в одном каталоге с исполняемым файлом.

3. **Запуск**:
   - Запустите исполняемый файл сервера. Сервер начнет слушать на `127.0.0.1:80`.
   - Для тестирования можно использовать любой HTTP-клиент, например, `curl` или браузер.

### Пример использования

- **GET запрос к `/`**: Вернет содержимое `index.html`.
- **POST запрос**: Сервер получит данные и выведет их в консоль, а затем отправит клиенту подтверждение получения.
- **PUT запрос**: Сохранит отправленные данные в файл `from PUT.txt`.
- **DELETE запрос**: Удалит указанный файл, если он существует.

### Обработка ошибок

Сервер обрабатывает ошибки при открытии и записи файлов, при отправке данных клиенту и при удалении файлов. Если возникает ошибка, она выводится в консоль, и сервер продолжает работу.
