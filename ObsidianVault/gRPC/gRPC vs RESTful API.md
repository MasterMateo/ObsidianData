#gRPC 

| **Feature**             |             **gRPC**             |       **RESTful**        |
| :---------------------- | :------------------------------: | :----------------------: |
| Контракт                |       Обязателено(.proto)        |        Опционален        |
| Протокол                |              HTTP/2              |        HTTP/2 & 1        |
| Payload                 |       Protobuf(небольшой)        |      JSON(большой)       |
| Сильно типизированный   |                да                |           нет            |
| Streaming               | Клиент, сервис, дву-направленный |      клиент, сервер      |
| Генерация кода клиентом |                да                | OpenAPI + стороняя инфр. |
| Безопасность            |          Transport(TLS)          |      Transport(TLS)      |
