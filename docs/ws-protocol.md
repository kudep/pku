# Протокол обмена с Socket.io

Используются не чистый WS протокол, а надстройка socket.io.

EntryPoint: [https://ds.readable.upgreat.one/pku](https://ds.readable.upgreat.one/pku)

ПКУ работает на socket.io реализации на nodejs.

# Сообщения WS сервера

-   **`connection-auth-error`**: ошибка авторизации

-   **`session-start-success`**: успех начала сессии. В payload прилетает id сессии.
-   **`session-start-error`**: ошибка начала сессии

-   **`session-reconnect-success`**: успех переподключения. В payload прилетает id сессии.
-   **`session-reconnect-error`**: ошибка переподключения

-   **`session-client-abort-success`**: успех остановки сессии
-   **`session-client-abort-error`**: ошибка остановки сессии

-   **`session-file-available`**: получение нового файла

-   **`session-close`**

    В payload прилетает `type`

    -   **`finish`**: сессия закрыта т.к. приняты все файлы
    -   **`timeout-close`**: закрытие сессии по таймауту 5 минут, последний файл отправлен сервером, но клиент не вернул один из файлов

В сообщения типа \*-error приходит сообщение с ошибкой.

# Сообщения WS клиента

-   **`session-start`**: начало сессии
-   **`session-reconnect`**: попытка переподключения к сессии
-   **`session-file-send`**: отправка файла
-   **`session-client-abort`**: остановка сессии
