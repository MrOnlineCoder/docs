## PosterTransport.stop: Остановить поиск устройств

> Пример остановки:

```kotlin
PosterTransport.start()
```

Останавливает поиск устройств. 
Метод не разрывает связь с уже подключенными устройствами, но при смене IP адреса и выключенном поиске, соединение будет потеряно. 
