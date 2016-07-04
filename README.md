# API плеера Рамблер/видео

API реализовано через интерфейс [postMessage](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage). Для прослушивания событий достаточно повесить на window обработчик события "message". Пример использования:

```javascript
function videoStartEventHandler() {
  console.log('Начало воспроизведения видео!');
}

window.addEventListener('message', function(event) {
  switch (event.data) {
    case 'rv_start':
      videoStartEventHandler();
      break;

    default:
      break;
  }
});
```

В данный момент возможно только получение некоторых событий. Сообщения отправленные в плеер не обрабатываются.

## Поддерживаемые события

| Событие       | Описание                                        |
| ------------- | ----------------------------------------------- |
| rv_init       | Происходит при инициализации плеера             |
| rv_start      | Происходит при начале воспроизведения ролика    |
| rv_end        | Происходит при окончании воспроизведения ролика |
| rv_preroll    | Происходит при начале воспроизведения преролла  |
| rv_postroll   | Происходит при начале воспроизведения постролла |
