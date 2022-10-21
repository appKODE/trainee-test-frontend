# Привет!

Это тестовое задание на стажировку в KODE. Набор на стажировку уже закончился, но сделать приложение в качестве практики для своего GitHub всё ещё можно.

Если хочешь, чтобы задание прошло ревью, то пиши [https://t.me/ekaterina_sergeeva1_en](@ekaterina_sergeeva1_en). Обычно мы даём ответ в течение 2 недель, но срок может увеличиться, если заявок будет много. Мы проверим задание и при возможности дадим краткий фидбэк, а если задание выполнено достаточно хорошо, то пригласим на интервью:)

Удачи!

## Что нужно сделать

В качестве тестового задания мы предлагаем тебе реализовать небольшое приложение, в котором есть всего по чуть-чуть: вёрстки, работы с API, преобразования данных и т. д.

## Какие требования к процессу и результату

1. Первое, что нужно сделать — это прочитать и разобраться во всех требованиях, дизайне и API, указанных в этом документе.
2. Затем разбить проект на отдельные задачи, то есть декомпозировать.
3. После этого дать временную оценку в часах каждой задаче. Если ожидаемое тобой время выполнения отдельной задачи превышает 2 часа, значит нужно эту задачу разбить на подзадачи и оценить каждую из них. В итоге у тебя должен получиться план работ и ожидаемое время выполнения всего тестового задания.
4. После планирования можно переходить к программированию. Создай новый репозиторий в GitHub, сделай его приватным (после старта стажировки можно будет его сделать публичным) и добавь в collaborators пользователя kode-frontend.
5. В первом commit в репозиторий в файле `readme.md` зафиксируй свой план задач с ожидаемой временной оценкой из пункта 3.
6. Двигаясь по собственному плану, реализуй тестовое задание.
7. По завершении работ добавь в `readme.md` реальное время выполнение задач и отправляй в ссылку на гитхаб к нам в бот [https://t.me/kodeFrontendBot](https://t.me/kodeFrontendBot)

### На что мы будем смотреть

- на полноту реализованного функционала и соответствие дизайну;
- количество ошибок;
- стиль и оформление кода;
- работу с git - оформление commits, pull requests;
- декомпозицию и оценку, то есть на твоё умение разбивать задачи и планировать собственное время;
- на что-то ещё :)

## Обязательный стэк

- Create React App
- React Router
- Axios

### Рекомендуется дополнительно использовать

- Typescript
- Effector \ redux
- styled-components

> - Рекомендованный стэк не ограничивает тебя по применению других технологий и библиотек.

## Дизайн

Хороший дизайн для клиентского разработчика — отличный способ быстро понять, что предстоит сделать. Не забываем, что вёрстка должна быть адаптивной!

[https://www.figma.com/file/GRRKONipVClULsfdCAuVs1/KODE-Trainee-Dev-Осень'21?node-id=11%3A14414](https://www.figma.com/file/GRRKONipVClULsfdCAuVs1/KODE-Trainee-Dev-%D0%9E%D1%81%D0%B5%D0%BD%D1%8C'21?node-id=11%3A14414)

## API

Спецификация метода API - [https://kode-frontend-team.stoplight.io/docs/koder-stoplight/e981f97438300-get-users-list](https://kode-frontend-team.stoplight.io/docs/koder-stoplight/e981f97438300-get-users-list)

### Получить всех пользователей

```javascript
const options = {
  method: "GET",
  headers: { "Content-Type": "application/json" },
};
fetch(
  "https://stoplight.io/mocks/kode-frontend-team/koder-stoplight/86566464/users?__example=all",
  options
)
  .then((response) => response.json())
  .then((response) => console.log(response))
  .catch((err) => console.error(err));
```

### Получить пользователей определённого департамента

```javascript
const options = {
  method: "GET",
  headers: { "Content-Type": "application/json" },
};
fetch(
  "https://stoplight.io/mocks/kode-frontend-team/koder-stoplight/86566464/users?__example=frontend",
  options
)
  .then((response) => response.json())
  .then((response) => console.log(response))
  .catch((err) => console.error(err));
```

> Параметр `__example` может принимать одно из значений:
> `android` `ios` `design` `management` `qa` `back_office` `frontend` `hr` `pr` `backend` `support` `analytics`

### Пример запроса для тестирования на разных данных (генерируется автоматически при каждом запросе)

```javascript
const options = {
  method: "GET",
  headers: { "Content-Type": "application/json" },
};

fetch(
  "https://stoplight.io/mocks/kode-frontend-team/koder-stoplight/86566464/users?__dynamic=true",
  options
)
  .then((response) => response.json())
  .then((response) => console.log(response))
  .catch((err) => console.error(err));
```

### Запрос, который вернёт ошибку с http кодом 500

```javascript
const options = {
  method: "GET",
  headers: { "Content-Type": "application/json" },
};
fetch(
  "https://stoplight.io/mocks/kode-frontend-team/koder-stoplight/86566464/users?__code=500&__dynamic=true",
  options
)
  .then((response) => response.json())
  .then((response) => console.log(response))
  .catch((err) => console.error(err));
```

## Функциональные требования

### Запуск

Когда пользователь открывает сайт, необходимо загрузить актуальный список всех работников компании.

При входе в приложение необходимо отобразить экран 2.0.0. Изначально он должен быть в состоянии загрузки, экран 1.0.0. Если при загрузке произошла ошибка, отсутствует интернет-соединение или API вернул ошибку, необходимо отобразить экран «Критическая ошибка». В случае успеха необходимо отобразить Top App Bar и список людей.

### Top App Bar

Компонент находится вверху экрана и представляет собой поле для поиска с иконкой «Поиск», кнопкой «Сортировка» и панелью вкладок. При переключении между вкладками на главном экране список работников фильтруется и отображаются только люди, работающие в выбранном департаменте, либо все, если выбрана вкладка «Все».

#### Возможны 2 вида реализации

1. **Простая.** Использовать фильтрацию пользователей на клиенте.
2. **Чуть сложнее.** Использовать серверную фильтрацию по параметру `__example`

##### Задание со звёздочкой

Рассказать о преимуществах и недостатках способов реализации.

#### Соответствия названия вкладок с полем "department" из запроса API:

```
android -> Android
ios -> iOS
design -> Дизайн
management -> Менеджмент
qa -> QA
back_office -> Бэк-офис
frontend -> Frontend
hr -> HR
pr -> PR
backend -> Backend
support -> Техподдержка
analytics -> Аналитика
```

При нажатии на кнопку «Фильтр» открывается модальное окно с вариантами сортировки списка работников. Есть два варианта сортировки: «По алфавиту» (по умолчанию), «По дню рождения». При переключении варианта сортировки модальное окно должно закрываться, а список на главной странице должен обновиться.

Когда пользователь вводит текст в поисковое поле, необходимо фильтровать список на главном экране и отображать только работников, соответствующих параметрам поиска. Поиск может осуществляться по имени, фамилии или никнейму, состоящему из двух символов.

В случае отсутствия результатов поиска необходимо отобразить информацию о том, что ничего не было найдено. Экран "2.0.2Г Люди (Ошибка поиска)"

### Страница «Главная»

На странице должна быть расположена верхняя панель приложения, на которой должны находиться:

- поле для поиска;
- панель вкладок для группировки загруженного списка пользователей;
- список работников.

Список должен обновляться каждый раз, когда меняются параметры поиска, обновляется вариант сортировки или пользователь переключает вкладки департаментов.

Пользователь имеет возможность скроллить список работников.

В режиме сортировки «По алфавиту» для каждого работника отображается его фотография, имя, никнейм и департамент.

В режиме сортировки «По дню рождения» список отображается от ближайшей даты дня рождения вниз. Если день рождения следующего работника будет только в следующем году, то необходимо отобразить блок с годом, экран 2.0.1.

Когда пользователь кликнет на человека, необходимо открыть экран информации о человеке (экран «детали»).

##### Задание со звёздочкой

Поиск, обновление списка должно происходить только после того, как пользователь закончил печатать.

### Страница «детали»

Должна быть реализована как отдельный роут в приложении.

Должна быть возможность попасть на страницу по ссылке.

Вверху экрана деталей должна отображаться кнопка назад для навигации на главный экран. Также можно вернуться на главный экран, если нажать кнопку назад в браузере.

В шапке экрана должна отображаться аватарка пользователя, имя, никнейм и название департамента.
Ниже находится дата рождения и номер телефона. При нажатии на номер телефона необходимо открыть приложение для звонка по номеру.

## Дополнительные задания

Дополнительные задания не обязательны для выполнения, но очень желательны. Если ты не успеваешь — лучше сделать хорошо основную часть. Но если время осталось...

### Реализовать real-time отслеживание состояния сети устройства

При отключении устройства от сети, верхняя панель приложения должна измениться на сообщение об ошибке сети, экран 2.0.0.А — Люди (Ошибка).
При этом должна остаться возможность пользоваться приложением в offline, теми данными, которые успели загрузится до отключения сети.

При восстановлении доступа к сети:

1. Верхняя панель приложения должна измениться на сообщение о загрузке, экран 2.0.0.А — Люди (Загрузка).
2. Список на активной вкладке должен обновиться.

### Сохранение состояния фильтрации и поиска

Ожидаемый результат:

- На главном экране выбрана сортировка «по дню рождения».
- Введена строка поиска.
- Отображается несколько результатов поиска.
- Пользователь переходит на экран «детали».
- Возвращается назад.
- Состояние поиска и сортировки сохранено.

### Кэширование результатов запроса по различным параметрам

Для запроса пользователей с параметром фильтра результат должен кэшироваться на клиенте на 5 минут.

Ожидаемый результат:

1. Переход на вкладку «Все»
   - Выполняется запрос без фильтрации.
2. Переход на вкладку «Дизайн»
   - Выполняется запрос с фильтрацией по полю department.
3. Переход на вкладку «Все»
   - До истечения 5 минут запрос не выполняется, данные отображаются из кэша.
   - После истечения 5 минут запрос выполняется, отображаются свежие данные.
4. Повторный переход на вкладку «Дизайн»
   - До истечения 5 минут запрос не выполняется, данные отображаются из кэша.
   - После истечения 5 минут запрос выполняется, отображаются свежие данные.

### На этом всё, желаем удачи!
