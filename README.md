# API плеера Рамблер/видео

API реализовано через интерфейс [postMessage](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage) и автоматически запускается в любом плеере вставленном через стандартный код вставки. Для прослушивания событий достаточно повесить на `window` обработчик события `"message"`. Пример использования:

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

| Событие         | Описание                         |
| --------------- | -------------------------------- |
| `rv_init`       | Инициализация плеера             |
| `rv_start`      | Начало воспроизведения ролика    |
| `rv_end`        | Окончание воспроизведения ролика |
| `rv_preroll`    | Начало воспроизведения преролла  |
| `rv_postroll`   | Начало воспроизведения постролла |
