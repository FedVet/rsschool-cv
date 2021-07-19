###### _Update as of 2021-07-18. Powered by google translator. Sorry. As my skills grow, I will add them._

## **Fedor Puntus**

### f.puntus@gmail.com

---

#### **Brief information.**

Current target: Front-end developer profession.\
Priorities: training, hands-on experience.\
Experience in IT: no.\
Positive qualities: Thanks to the main job (veterinarian)
I developed such qualities as perseverance, learning ability, ability to work under stressful conditions.

#### **Skills**

HTML and CSS basics

#### **Code examples**

## My code from the [HTML and CSS Basics](https://www.coursera.org/learn/snovy-html-i-css/home/info) course assignment

###### _I know he's not perfect_

```
<!DOCTYPE html>
<html lang="ru">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title>Блог компании Яндекс</title>
</head>
<!-- CSS использовал по минимуму, дабы по возможности привести в соответствии со стилитикой задания -->
<body>
    <header>
        <h1>Блог компании Яндекс.</h1>
    </header>
    <main>
        <article>
            <h2 >ЯНДЕКС.ПОЧТА: КАК МЫ ИЗМЕРЯЕМ СКОРОСТЬ ЗАГРУЗКИ И УЛУЧШАЕМ ЕЁ</h2>
            <p >
                Если ваш сайт медленно грузится, вы рискуете тем, что люди не оценят ни то,
                какой он красивый, ни то, какой он удобный. Никому не понравится, когда все
                тормозит. Мы регулярно добавляем в Яндекс.Почту новую функциональность,
                иногда — исправляем ошибки, а это значит, у нас постоянно появляются новый код
                и новая логика. Всё это напрямую влияет на скорость работы интерфейса.
            </p>
            <h3>Что мы измеряем</h3>
            <h4>Этапы первой загрузки:</h4>
            <ul style= "list-style-type: none;">
                <li>&#9913;	подготовка;</li>
                <li>&#9913;	загрузка статики (HTTP-запрос и парсинг);</li>
                <li>&#9913;	исполнение модулей;</li>
                <li>&#9913;	инициализация базовых объектов;</li>
                <li>&#9913;	отрисовка.</li>
            </ul>
            <h4>Этапы отрисовки любой страницы:</h4>
            <ul style= "list-style-type: none;">
                <li>&#9913;	подготовка к запросу на сервер;</li>
                <li>&#9913;	запрос данных с сервера;</li>
                <li>&#9913;	шаблонизация;</li>
                <li>&#9913;	обновление DOM.</li>
            </ul>
            <p>
                &ndash;<q style="quotes: '«' '»';">Ок, теперь у нас есть метрики, мы можем отправить их на сервер</q> - говорим мы<br>
                &ndash;<q style="quotes: '«' '»';">Что же дальше?</q> - вопрошаете вы<br>
                &ndash;<q style="quotes: '«' '»';">А давай построим график!</q> - отвечаем мы<br>
                &ndash;<q style="quotes: '«' '»';">А что будем считать?</q> - уточняете вы<br>
            </p>
            <p>
                Как вы знаете, <dfn>медиана</dfn> – это <em>серединное</em>, а не среднее значение в выборке.
                Если у нас имеются числа 1, 2, 2, 3, 8, 10, 20, то медиана – 3, а среднее – 6,5.
                В общем случае медиана отлично показывает, сколько грузится средний пользователь.
            </p>
            <p>
                В случае ускорения или замедления медиана, конечно, изменится. Но она не может
                рассказать, сколько пользователей ускорилось, а сколько замедлилось.
            </p>
            <p>
                <abbr title="Application Performance Index" style="text-decoration: none;">
                    <dfn>APDEX</dfn>
                </abbr> – метрика, которая сразу говорит: хорошо или плохо. Метрика
                работает очень просто. Мы выбираем временной интервал <var>[0; t]</var>, такой, что если
                время показа страницы попало в него, то пользователь счастлив. Берем еще один
                интервал, <var>(t; 4t]</var> (в четыре раза больше первого), и считаем, что если страница
                показана за это время, то пользователь в целом удовлетворен скоростью работы,
                но уже не настолько счастлив. И применяем формулу:
            </p>
            <p>
                <code>
                    (кол-во счастливых пользователей + кол-во удовлетворенных / 2) / (кол-во всех)
                </code>.
            </p>
            <p>
                Получается значение от нуля до единицы, которое, видимо, лучше всего показывает,
                хорошо или плохо работает почта.
            </p>
            <h3>Как мы измеряем</h3>
            <p>
                Сейчас модуль обновления сам логирует все свои стадии, и можно легко понять
                причину замедления: медленнее стал отвечать сервер либо слишком долго
                выполняется JavaScript. Выглядит это примерно так:
            </p>
            <pre>
                <code>
                    this.timings['look-ma-im-start'] = Date.now();
                    this.timings['look-ma-finish'] = Date.now();
                </code>
            </pre>
            <p>
                C помощью <code>Date.now()</code> мы получаем текущее время. Все тайминги собираются и при
                отправке рассчитываются. На этапах разница между <em>“end”</em> и <em>“start”</em> не считается,
                а все вычисления производятся в конце:
            </p>
            <pre>
                <code>
                    var totalTime = this.timings['look-ma-finish'] - this.timings['look-ma-im-start'];
                </code>
            </pre>
            <p>
                И на сервер прилетают подобные записи:
            </p>
            <pre>
                <samp>
                    serverResponse=50&domUpdate=60
                </samp>
            </pre>
            <h3>Как мы ускоряем</h3>
            <h4>Чтобы снизить время загрузки почты при выходе новых версий, мы уже делаем следующее:</h4>
            <ul style= "list-style-type: none;">
                <li>&#9913;	включаем gzip;</li>
                <li>&#9913;	выставляем заголовки кэширования;</li>
                <li>&#9913;	фризим CSS, JS, шаблоны и картинки;</li>
                <li>&#9913;	используем CDN;</li>
            </ul>
            <p>
                Мы подумали: <q>А что если хранить где-то старую версию файлов, а при выходе новой
                передавать только <em>diff</em> между ней и той, которая сохранена у пользователя?</q>
                В браузере же останется просто наложить патч на клиенте.
            </p>
            <p>
                а самое деле эта идея не нова. Уже существуют стандарты для <em>HTTP</em> — например,
                <em>RFC 3229</em> <q style="quotes: '«' '»';"><em>Delta encoding in HTTP</em></q> и <q style="quotes: '«' '»';"><em>Google SDHC</em></q>, — но по разным причинам они
                не получили должного распространения в браузерах и на серверах.
            </p>
            <p>
                Мы же решили сделать свой аналог на <em>JS</em>. Чтобы реализовать этот метод обновления,
                начали искать реализации <em>diff</em> на <em>JS</em>. На популярных хостингах кода нашли
                библиотеки:
            </p>
            <ul style= "list-style-type: none;">
                <li><a style=" text-decoration: none;" href="">&ndash;	VCDiff</a></li>
                <li><a style=" text-decoration: none;" href="">&ndash;	google-diff-patch-match</a></li>
            </ul>
            <h4>Для окончательного выбора библиотеки нам нужно сравнить:</h4>
            <table>
                <thead>
                <tr>
                	<td>Библиотека</td>
                	<td>IE 8</td>
                	<td>Opera 12</td>
                </tr>
                </thead>
                <tbody>
                <tr>
                	<td>vcdiff</td>
                	<td>8</td>
                	<td>5</td>
                </tr>
                <tr>
                	<td>google diff</td>
                  <td>1363</td>
                  <td>76</td>
                </tr>
                </tbody>
            </table>
            <p>
                После того как мы определились с библиотекой для диффа, нужно определиться с тем,
                где и как хранить статику на клиенте.
            </p>
            <h4>Формат файла с патчами для проекта выглядит так:</h4>
            <pre>

                [
                    {
                        "k": "jane.css",
                        "p": [patch],
                        "s": 4554
                    },
                    {
                        "k": "jane.css",
                        "p": [patch],
                        "s": 4554
                    }
                ]
            </pre>
            <p
            >
                То есть это обычный массив из объектов. Каждый объект — отдельный ресурс. У
                каждого объекта есть три свойства. <var>k</var> — названия ключа в <em>localStorage</em> для этого
                ресурса. <var>p</var> — патч для ресурса, который сгенерировал <em>vcdiff</em>. <var>s</var> — чексумма для
                ресурса актуальной версии, чтобы потом можно было проверить правильность
                наложения патча на клиенте. Чексумма вычисляется по <cite>алгоритму Флетчера</cite>.
            </p>
            <p>
                <dfn>Алгоритм Бройдена — Флетчера — Гольдфарба — Шанно (<abbr title="Бройдена — Флетчера — Гольдфарба — Шанно" style="text-decoration: none;">
                    BFGS
                </abbr>)</dfn>
                — итерационный метод численной оптимизации, предназначенный для
                нахождения локального максимума/минимума нелинейного функционала
                без ограничений.
            </p>
            <h4>Алгоритм Флетчера:</h4>
            <p>
                Дано &epsilon;, x<sub>0</sub><br>
                Инициализировать &Eta;<sub>0</sub><br>
                k = 0<br>
                while ||&nabla;&fnof;|| > &epsilon;<br>
                &emsp;найти направление p<sub>k</sub> = &ndash;C<sub>k</sub>&nabla;&fnof;<sub>k</sub>;<br>
                &emsp;вычислить s<sub>k</sub> = x<sub>k+1</sub> &ndash; x<sub>k</sub>;
                &emsp;и y<sub>k</sub> = &nabla;&fnof;<sub>k+1</sub> &ndash; &nabla;&fnof;<sub>k</sub>;<br>
                &emsp;вычислить C<sub>k+1</sub>;<br>
                &emsp;k = k + 1;<br>
                end
            </p>
            <h4>Почему именно алгоритм Флетчера, а не другие популярные алгоритмы вроде:</h4>
            <dt>
                <dl>CRC16/32</dl>
                <dd>алгоритм нахождения контрольной суммы, предназначенный для проверки
                    целостности данных
                </dd>
                <dl>md5</dl>
                <dd>128-битный алгоритм хеширования. Предназначен для создания «отпечатков»
                    или дайджестов сообщения произвольной длины и последующей проверки
                    их подлинности.
                </dd>
            </dt>
            <p>Потому что он быстрый, компактный и легок в реализации.</p>
            <h3>Итог</h3>
            <table>
                <thead>
                	<tr>
                		<td>Релиз</td>
                 		<td>С патчем</td>
                  	<td>Без патча</td>
                  </tr>
                </thead>
                <tbody>
                 <tr>
                	<td>7.7.20</td>
                  <td>397</td>
                  <td>174 549</td>
                 </tr>
                <tr>
                	<td>7.7.21</td>
                	<td>383</td>
                	<td>53 995</td>
                </tr>
                <tr>
                	<td>7.7.22</td>
                	<td>483</td>
                	<td>3 995</td>
                </tr>
                </tbody>
            </table>
            <hr>
            <footer>
                <address>
                    Автор: @doochik<br>
                    С++ разработик<br>
                    Электронная почта: <a style=" text-decoration: none;" href="mailto:doochik@yandex.ru">doochik@yandex.ru</a><br>
                    Компания: Яндекс
                </address>
            </footer>
        </article>
        <br>
        <article>
            <h3>Комментарии (3):</h3> <!-- Коментариев по ходу 4, но коль скоро в задании написано 3 то оставил 3 :) -->
            <ul style= "list-style-type: none;">
                <li>&ndash; Mogaika<a style=" text-decoration: none;" href="mailto:mogaika@yandex-team.ru">(mogaika@yandex-team.ru)</a><time datetime="2014-11-30T17:05:00Z">30 ноября 2014 в 17:05</time><br>
                    А можете привести сравнение, на сколько быстрее грузится lite версия?
                </li>
                <li>&ndash; JIguse<a style=" text-decoration: none;" href="mailto:mrawesome@yandex.ru">(mrawesome@yandex.ru)</a><time datetime="2014-11-29T21:30:00Z">29 ноября 2014 в 21:30</time><br>
                    Спасибо за статью, познавательно. Здорово, что Яндекс делится некоторыми подробностями о внутренней работе сервисов.
                </li>
                <li>&ndash;Brister<a style=" text-decoration: none;" href="mailto:brist89@yandex-team.ru">(brist89@yandex-team.ru)</a> <time datetime="2014-11-24T13:13:00Z">24 ноября 2014 в 13:13</time><br>
                   <blockquote>
                     (кол-во счастливых пользователей + кол-во удовлетворенных / 2) / (кол-во всех). Получается значение от нуля до единицы, которое, видимо, лучше всего показывает, хорошо или плохо работает почта.
                  </blockquote><br>
                     наверное все-таки от 0.5 до 1
                </li>
                <li>&ndash;alexeimois<a style=" text-decoration: none;" href="mailto:test@yandex.ru">(test@yandex.ru)</a><time datetime="2014-11-22T17:35:00Z">22 ноября 2014 в 17:35</time><br>
                	Мы измеряем скорость загрузки с помощью<a style=" text-decoration: none;" href="http://help.yandex.ru/metrika/reports/monitoring_timing.xml">Яндекс.Метрики</a>
                </li>
             </ul>
          </article>
             </main>
    <footer>
        <address>© Яндекс, <a style=" text-decoration: none;" href="mailto:help@yandex.ru">help@yandex.ru</a>, Хохрякова, 10</address>
    </footer>
</body>
</html>
```

#### **Work experience.**

General Veterinarian 2007-present.

#### **Education**

Education is a higher level, graduating from the Saint-Petersburg State University of Veterinary Medicine (2007)\
Completed the course [Introduction to CSS3](https://www.coursera.org/account/accomplishments/certificate/3WXYXJB6RQ3H) on the platform coursera.
Completed the course [Introduction to HTML5](https://www.coursera.org/account/accomplishments/certificate/T7XNPTMTGE66) on the platform coursera.\
Completed the course [Interactivity with JavaScript](https://www.coursera.org/account/accomplishments/certificate/QJURPSZJABKY) on the platform coursera.\
I am learning JavaScript / Front-end in RSSchool

#### **English language**
A0-A1

