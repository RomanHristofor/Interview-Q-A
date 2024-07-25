# Interview-Q-A

## Какие существуют методы оптимизации производительности в JS?
 Вот некоторые методы оптимизации:

1. Использование let и const вместо var:
let и const имеют блочную область видимости, что позволяет более точно контролировать область видимости переменных
 и избегать нежелательных эффектов.

2. Избегание глобальных переменных:
Глобальные переменные могут вызывать конфликты и усложнять отладку. Старайтесь минимизировать использование
 глобального пространства имен.

3. Оптимизация циклов:
Используйте схемы оптимизации циклов, такие как предварительное вычисление длины
```for (let i = 0, len = array.length; i < len; i++)```
или использование методов массивов: forEach, map, filter, вместо явных циклов.

5. Кэширование переменных:
Если вы часто обращаетесь к одному и тому же объекту, то имеет смысл закешировать его в переменной,
 чтобы избежать повторных обращений.

6. Использование строгого равенства (===) вместо нестрогого (==):
Строгое равенство не приводит типы, что уменьшает вероятность неявных преобразований и может ускорить выполнение кода.

7. Использование массивов вместо объектов для хранения упорядоченных данных:
Для операций, требующих поиска по индексу, массивы часто более эффективны.

8. Оптимизация работы с DOM:
Минимизируйте количество обращений к DOM. Используйте методы типа `querySelector` для эффективного поиска элементов.

9. Делегирование событий:
Используйте `делегирование событий` для оптимизации работы с большим количеством элементов.
 Вместо присоединения обработчиков к каждому элементу, присоединяйте их к их общему родителю.

10. Оптимизация работы с циклами и рекурсией:
Важно оптимизировать алгоритмы и убедиться, что они работают с максимальной эффективностью.

11. Минимизация запросов к серверу и оптимизация загрузки ресурсов:
Сокращение числа запросов к серверу, минификация и сжатие файлов, асинхронная загрузка ресурсов
 и другие методы могут существенно повысить производительность веб-приложения.

12. Использование `Web Workers` и `Service Workers`:
Позволяют выполнять вычисления в отдельных потоках и кэшировать ресурсы для улучшения производительности.

13. Использование инструментов для анализа и профилирования кода:
Инструменты, такие как `Chrome DevTools`, позволяют выявить узкие места в коде и оптимизировать их.

Важно помнить, что оптимизация не всегда означает уменьшение количества кода,
а скорее - повышение эффективности его работы. 
Выбор методов оптимизации зависит от конкретной задачи и контекста разработки.


## CORS
Cross-Origin Resource Sharing — это механизм в веб-браузерах, который позволяет ограничивать
 или разрешать запросы к ресурсам с других источников (origin) в веб-приложениях.
Origin включает в себя схему (например, http или https), домен и порт.

Когда веб-страница загружается из одного `origin` и пытается выполнить запрос к ресурсу (например, JavaScript-файлу или API) на другом
 `origin`, браузер использует механизмы безопасности, в том числе `CORS`, чтобы решить, разрешено ли выполнение этого запроса.

Вот основные аспекты `CORS`:
`Простые запросы (Simple Requests)`: Обычные HTTP-запросы методом GET, HEAD и POST с определенными заголовками считаются "простыми" и
 по умолчанию разрешаются. Простые запросы могут быть выполнены без предварительной проверки сервера.
`Непростые запросы (Non-Simple Requests)`: Если запрос отличается от простого (например, использует метод PUT или DELETE,
 или имеет определенные кастомные заголовки), браузер сначала отправит предварительный запрос с методом `OPTIONS (preflight request)`
  для уточнения, разрешено ли такое действие. Сервер должен ответить с соответствующими заголовками, разрешая или запрещая запрос.

`Заголовки CORS`: Сервер может отправить специальные заголовки в ответе для указания правил `CORS`. Например, заголовок `Access-Control-Allow-Origin`
 указывает, каким источникам разрешено делать запросы.
`Методы запроса`: Методы запросов, которые разрешены для данного ресурса, указываются с помощью заголовка `Access-Control-Allow-Methods`.
`Заголовки запроса`: Заголовки, которые разрешено передавать в запросе, указываются с помощью заголовка `Access-Control-Allow-Headers`.

`Управление куки`: По умолчанию, при кросс-доменных запросах не отправляются куки. Если сервер хочет принимать куки, он должен указать
 заголовок `Access-Control-Allow-Credentials` и клиент должен установить соответствующую опцию `withCredentials` в запросе.

`Проверка запросов (Preflight)`: В некоторых случаях браузер может отправить предварительный запрос `preflight с методом OPTIONS,
 чтобы уточнить, разрешено ли выполнение основного запроса. Это происходит, когда запрос считается "непростым".

`Wildcard (Знак мультиподстановки)`: Заголовок `Access-Control-Allow-Origin` может принимать значение *, что разрешает доступ 
всем источникам. Однако, это считается менее безопасным и используется в особых случаях.

`CORS` позволяет веб-страницам взаимодействовать с ресурсами с других источников, но в то же время предотвращает выполнение запросов
 с злоумышленных сайтов. Он важен для обеспечения безопасности веб-приложений.

## Куки
`cookies` в веб-разработке - это небольшие фрагменты данных, которые веб-сайты сохраняют на устройстве пользователя.
Они играют ключевую роль в современном интернете, выполняя различные функции. 
 Вот несколько основных аспектов и использований куки:
`Хранение Сессий`: Куки часто используются для отслеживания сессий пользователей. Когда пользователь входит на сайт,
   сервер может создать уникальный идентификатор сессии и сохранить его в куки. Это позволяет серверу идентифицировать
    пользователя при каждом последующем запросе, сохраняя его состояние входа в систему.
`Персонализация`: Сайты используют куки для хранения персональных настроек пользователя, таких как выбранный язык,
   тема оформления или предпочтения в содержании. Это обеспечивает более персонализированный пользовательский опыт.
`Отслеживание и Аналитика`: Куки помогают в сборе данных о поведении пользователя на сайте. Эта информация может использоваться
   для аналитики, помогая понять, как пользователи взаимодействуют с сайтом, что в свою очередь может способствовать улучшению
    веб-сервисов.
`Реклама`: Куки используются для отслеживания пользовательской активности в интернете, что позволяет рекламодателям показывать
   более целевую и релевантную рекламу. Это может включать рекламу, основанную на недавних поисках или посещенных веб-страницах.
  `Безопасность`: Куки могут использоваться для повышения безопасности сайта, например, для предотвращения подделки 
  межсайтовых запросов (CSRF). Они могут содержать токены безопасности, которые проверяются сервером при каждом запросе.

**Типы Куки**:
`Сессионные куки`: Эти куки хранятся только во время сессии браузера и удаляются автоматически, когда браузер закрывается. 
  Они обычно используются для отслеживания сессий пользователя.
`Постоянные куки`: Эти куки сохраняются на устройстве пользователя в течение определенного времени, указанного в куки, 
  или до тех пор, пока они не будут удалены пользователем. Они используются для сохранения предпочтений пользователя и отслеживания
   поведения на долгосрочной основе.
`Управление и Конфиденциальность`: Пользователи и браузеры имеют возможность управлять куки, включая возможность блокировки
   или удаления их. Это важный аспект конфиденциальности, так как куки могут содержать чувствительные данные.

`cookies` могут иметь различные `атрибуты`, влияющие на их поведение и доступность. Один из таких атрибутов - `HttpOnly`,
 который иногда называют "readonly" кукой. Он имеет ключевое значение для безопасности веб-приложений.

`HttpOnly (Readonly) Cookie`:
`Ограничение Доступа`: Когда кука помечена как `HttpOnly`, это означает, что она недоступна для клиентских скриптов,таких как JavaScript.
Такая кука может быть отправлена только на сервер с `HTTP-запросами`.
`Защита от XSS-атак`: Основная цель `HttpOnly` куки - защита от кросс-сайтовых скриптинговых атак (XSS). При таких атаках
  злоумышленники могут вставлять `вредоносный код в веб-страницы`, который исполняется в браузере жертвы. 
Если куки содержат `чувствительные данные, такие как сессионные токены`, и они не защищены атрибутом `HttpOnly`,
вредоносный скрипт может прочитать эти куки и отправить данные злоумышленнику.

В целом, куки являются важным инструментом для обеспечения бесперебойной и персонализированной работы в интернете,
 но также вызывают опасения по поводу конфиденциальности и безопасности данных.

## SQL-инъекции, XSS атаки
*`SQL-инъекци`я — это тип атаки, при которой злоумышленник вводит вредоносные SQL-запросы через веб-формы или URL-адреса,
 что может привести к несанкционированному доступу к базе данных.

Пример безопасного запроса:
`SELECT * FROM users WHERE username='john' AND password='12345';`

Пример уязвимого запроса, подверженного SQL-инъекции:
`SELECT * FROM users WHERE username='' OR 1=1; --' AND password='12345';`
В данном примере, если не проводить адекватную фильтрацию входных данных, злоумышленник может ввести `' OR 1=1; --`
 в поле "username", что приведет к тому, что условие 1=1 всегда будет верным, и запрос вернет все строки из таблицы.

Чтобы предотвратить SQL-инъекции, следует использовать параметризованные запросы
 или подготовленные запросы, а не встраивать пользовательский ввод непосредственно в SQL-запросы.

*`XSS-атаки` (Cross-Site Scripting):
XSS-атаки — это атаки, при которых злоумышленник внедряет вредоносный JS-код в веб-страницу,
 который выполняется в браузере жертвы. Атаки могут быть сохраненными (persistent) или рефлектированными (reflected).

Сохраненные (Persistent) XSS:
При сохраненных XSS-атаках, зловредный код сохраняется на сервере и выполняется при каждом запросе к соответствующей странице.

Пример уязвимого места:
`<input type="text" value="USER_INPUT">`
Если при вводе данных в поле USER_INPUT не проводится должная фильтрация, злоумышленник может ввести JS-код,
 который будет выполнен в браузере всех пользователей, открывших эту страницу.

*Рефлектированные (Reflected) XSS:
При рефлектированных XSS-атаках, зловредный код внедряется в URL или форму и выполняется при загрузке страницы.
 Эти атаки зависят от того, что жертва перейдет по определенной ссылке.
Пример уязвимого URL:
```https://example.com/search?query=USER_INPUT
// Предполагаем, что userInput содержит ввод пользователя
const userInput = "некоторый_пользовательский_ввод";
// encodedUserInput будет содержать правильно закодированное значение
const encodedUserInput = encodeURIComponent(userInput);
// USER_INPUT, которое можно безопасно добавить к URL.
const url = https://example.com/search?query=${encodedUserInput};
```

Если значение USER_INPUT не экранируется или фильтруется некорректно, зловредный код может
 быть выполнен в контексте страницы.

Для предотвращения XSS-атак следует проводить валидацию и фильтрацию данных, а также использовать
 безопасные методы для вставки данных в HTML, такие как эскейпинг специальных символов (<, >, &, и так далее).

*`Cross-Site Request Forgery (CSRF)` Атака, заставляющая веб-браузер жертвы выполнять нежелательные действия на веб-сайте, на котором она аутентифицирована.
Предположим, что на веб-сайте есть следующая форма для изменения email-адреса:
```<!-- Пример уязвимой формы на веб-сайте -->
<form action="http://example.com/update-email" method="POST">
  <input type="email" name="newEmail" />
  <input type="submit" value="Изменить Email" />
</form>
```

Как Происходит CSRF-Атака?
1)Подготовка Атакующим Запроса:

Злоумышленник создает вредоносную веб-страницу или email с HTML-кодом, который автоматически 
отправляет POST-запрос на `example.com/update-email`, когда жертва загружает страницу или открывает email.

```<!-- Вредоносная веб-страница или email -->
<html>
  <body>
    <form action="http://example.com/update-email" method="POST" id="fakeForm">
      <input type="hidden" name="newEmail" value="attacker@example.com" />
    </form>
    <script>document.getElementById("fakeForm").submit();</script>
  </body>
</html>
```

2)Выполнение Запроса:
Когда пользователь, который аутентифицирован на `example.com`, открывает эту вредоносную страницу или email,
форма автоматически отправляется. Поскольку запрос отправляется с аутентификационными данными пользователя
(например, сессионными cookies), сервер `example.com` обрабатывает его как законный и изменяет email-адрес пользователя на адрес злоумышленника.

3)Защита от CSRF
Для защиты от CSRF-атак обычно используются токены, которые сервер встраивает в формы и проверяет при получении запросов:
```<form action="http://example.com/update-email" method="POST">
  <!-- Сервер генерирует уникальный токен и встраивает его в форму -->
  <input type="hidden" name="csrfToken" value="сгенерированный_уникальный_токен" />
  <input type="email" name="newEmail" />
  <input type="submit" value="Изменить Email" />
</form>
```
Сервер затем проверяет этот токен при обработке запроса. Если токен отсутствует или неверен, запрос отклоняется. Это предотвращает
 CSRF-атаки, поскольку злоумышленник не может знать или подделать токен, который генерируется сервером и является уникальным для
  каждой сессии пользователя.
Кроме того, для защиты от CSRF можно использовать такие меры:
*Проверка Заголовка Referer: Сервер может проверять заголовок HTTP Referer, чтобы убедиться, что запрос отправлен с доверенного
 источника.
*Использование Сookie с Флагом SameSite: Установка флага SameSite для куки помогает предотвратить отправку куки с запросами,
 инициированными с других сайтов.
*Реализация Подтверждения Действий: Для критически важных операций требовать от пользователя подтверждения действия,
 например, введения пароля или дополнительного кода подтверждения.
Эти методы помогают минимизировать риск CSRF-атак, обеспечивая более высокий уровень безопасности веб-приложений.
















