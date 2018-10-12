# Какие бывают языки

Помните я как-то говорил, что самый простой способ учить языки - это понять различия между ними? Именно для этого я и пробегусь вкратце по основным особенностям, которые встречаются у языков программирования (или, по крайней мере, которые встречал я). Плюс это будет хорошим подспорьем - ничто так не упрощает ныряние с головой в океан, как знание местности.

Итак, какие же бывают языки и как их можно классифицировать?

## По типу исполнения

Помните такое классное слово - компилятор? Да, я не по приколу упоминал его в предыдущей лекции, описывая историю развития языков программирования. Там я рассказал, что для запуска программного кода его сперва необходимо преобразовать в машинный. Но что, если есть другой вариант?

Итак, по типу исполнения языки бывают:

### Компилируемые
**Пример:** C/C++, Go, Rust

Языки, программный код которых для исполнения преобразовывается компилятором в аппаратнозависимый машинный код. Еще не так давно это был основной класс языков. Программы, написанные на компилируемом языке, быстрые, оптимальные, имеют прямой доступ к памяти (по крайней мере могут, если подобные идеи заложены в исполнение языка) и... являются довольно небезопасными. Прямой доступ к ресурсам компьютера делает их, во-первых, довольно уязвивыми к так называемой "проблеме стрельбы по собственным ногам" - когда программист, сам того не желая, реализует функционал, нарушающий нормальную работу системы. В современных системах это не так просто, так как эти самые современные системы обладают широкими возможностями в защите ног пользователя от попаданий. Каждая программа работает не с физической, а с виртуальной выделенной памятью, к примеру. Однако, как говорил Рик Кук, "Программирование сегодня - это гонка разработчиков программ, стремящихся писать программы с большей и лучшей идиотоустойчивостью, и вселенной, которая пытается создать больше отборных идиотов. Пока вселенная побеждает". К сожалению, разработчики тоже не всегда гении.
Подводя итог:

**Плюсы:** 
 - Относительная простота реализации
 - Скорость исполнения
 - Прямой доступ к ресурсам системы

**Минусы:**
 - Аппаратная зависимость скомпилированной программы (да и исходного кода зачастую)
 - Возможность стрельбы по собственным ногам

### Интерпретируемые языки

**Примеры:** Java, Python, JS

Но что, если перестать компилировать код? Что, если программный код будет исполнять другая программа? 

Именно этим вопросам интерпретируемые языки и обязаны своему появлению. Основное отличие интерпретируемых языков от компилируемых - последние нетранслируются не в машинный код, а в какую-либо промежуточную форму, которая в дальнейшем исполняется спкциальной программой - интерпретатором. Подобная программа является так называемой "средой исполнения" - своеобразной прослойкой между операционной системой и испольняемым кодом. Подобная прослойка в значительной мере уменьшает связность между ОС и программой, что делает инетрпретируемые языки зачастую более безопасными и менее удобными для стрельбы по ногам. Обращения к памяти, к примеру, сперва проходят через среду исполнения, и только потом добираются до самой ОС. Таким образом, если эти обращения некорректные - первым делом отваливается сам интерпретатор, а до ОС эти некорректные вызовы зачастую даже не добираются. 

Еще одна положительная сторона интерпретируемых языков - аппаратная независимость. Один и тот же код может быть запущен на любой архитектуре, если для нее написана среда исполнения.

Однако за все это разнообразие прекрасных положительных моментов приходится платить. В данном случае, платить скоростью исполнения. Будучи, по сути, посредником между программой и ОС, интерпретатор не может не замедлять программу и не усложнять ее работу.

**Плюсы:** 
 - Аппаратная независимость
 - Сравнительно большая безопасность

**Минусы:**
 - Скорость исполнения.

Не смотря на кажущуюся пропасть, лежащую между этими типами, довольно много современных языков являются одновременно и компилируемыми, и интерпретируемыми. Это позволяет произовдить быстрое прототипирование, когда это необходимо, а так же добиваться высокой скорости исполнения, когда это необходимо.

## По уровню

Под уровнем языка обычно понимается:

 - Степень отличия от машинного кода
 - Степень, в которой семантика языка учитывает особенности мышления человека

Говоря простыми словами, чем более язык, так сказать, "человекопонятен" - тем выше его уровень. То бишь если вы видите что-то в стиле

```python
for person in crowd:
    print(person.name)
```

то это явно высокоуровневый. А вот если

```assembly
.text
main:
    la  $s0, A
    lw  $s0, 0($s0)
    la  $s1, B
    lw  $s1, 0($s1)

    add $s2, $s0, $s1
    la  $s3, Sum
    sw  $s2, 0($s3)
```

то это определенно низкоуровневый. 

### Низкоуровневые языки

**Примеры:** ассемблер

О них я мельком упоминал в истории языков. Это языки, близкие компьютеру, далекие от человека (по крайней мере, от основной массы человечества), используются там, где разработка происходит рядом с железом - драйвера, контроллеры для различных устройств, ядра ОС, файловая система и т.д. и т.п.

**Плюсы:**
 - Очень высокая скорость работы. Еще бы - вы говорите машине что ей делать на ее собственном языке!

**Минусы:**
 - Высокая сложность в понимании подобных программ человеком.

### Высокоуровневые языки

**Примеры:** Java, C#, Python, JS, куча их

Основная масса языков на данный момент. Близки и удобны для человека, после компиляции\в процессе интерпретации превращаются в машинный код, удобны в разработке.

**Плюсы:**
 - Сделаны людьми для людей, благодаря чему сравнительно понятны

**Минусы:**
 - В основном медленне, чем низкоуровневые языки, и не имеют такого доступа к ресурсам системы. 

## По способу типизации

Типизация - крайне важная штука в любом языке, так как она управляет памятью. Что же такое типизация?

Представьте, что вы переезжаете. У вас дома множество емкостей. Самых разных. Картонные коробки, пластиковые контейнеры, ведра там и прочая фигня. А еще у вас есть куча разной ерунды - еда, которую вы уже приготовили, еще не сьели, но очень хотите. Кофе, которое вы сварили, и которое вам очень жаль выливать. А еще посуда, одежда, книги, техника и прочее. А еще у вас есть не очень умный друг, которому вы заплатили пятнадцать баксов, чтобы он расфасовал ваши вещи по емкостям, потому что вы, мягко говоря, очень ленивый человек.

Проблема в том, что не очень умный друг постоянно порывается запихивать предметы в не очень подходящие емкости. Еду в картонную коробку, одежду в пластиковые контейнеры для еды, и так далее. Для того, чтобы избежать проблем в дальшейшем, вы взяли да и подписали все емкости. На большой картонной коробке написали **одежда**, на деревянном ящике - **техника**, на контейнере для еды - **еда**. Теперь, когда ваш не очень умный друг попытается засунуть что-то в какую-либо емкость - он сперва проверит подпись, и не зальет случайно кофе в ящик. Таким образом, вы избавились от проблем.

Но вы могли пойти и другим путем. Съездить в ближайший магазин, закупить больших герметичных пластиковых контейнеров, и сказать своему не очень умному другу - "суй в любой что хочешь, мне по факту без разницы. Они герметичные, хорошо закрываются, и мне без разницы, что будет внутри - еда, одежда, книги, техника или та кружка кофе, чтоя почему-то решил везти с собой, вместо того, чтобы выпить. А еще они прозрачные - и я в любой момент вижу, что находится внутри". 

Так вот, в данной метафоре емкости - это переменные, содержимое емкостей - данные, а подписи на емкостях - это типы данных. С помощью типов данных программист указывает компилятору\интерпретатору, какие данные можно совать в переменные, а какие нет. К примеру, в языке Java подобный код

```java
int i = "kek lol";
```

вызовет ошибку исполнения, так как Java - **строго типизированный язык**, int - тип, означающий целое число, а мы пытаемся засунуть в него строку. Так и с подписанными емкостями и не очень умным другом - тот будет совать вещи только в емкость, подписанную нужным образом. 

А к чему второй пример, спросите вы? К тому, что помимо строго типизированных языков есть еще и **динамически типизируемые**. Это значит, что при создании переменной язык еще не знает, какого типа эта переменная должна быть, и определяет ее тип только при присвоении значения. К примеру, вот код на Python:

```python
i = "kek lol"
```

Как вы видите, мы вообще не указываем тип переменной, потому что языку без разницы, что за данные в ней будут хранится. Прямо как с большими пластиковыми контейнерами. 

Существенным плюсом строго типизированных языков является упрощение отладки. Неверные данные, случайно засунутые не в ту переменную похожи на террориста-смертника с огромным запасом терпения. Они будут выжидать, выжидать долго, и по итогу взорвуться с криком типа "смерть динамической типизации!", нанеся максимальный урон, просто потому, что решать проблему с их существованием будет уже поздно. Особо радуют неправильные данные, занесенные в базу данных.

Однако скорость разработки на динамически типизируемых языках обычно несколько выше. Динамически типизируемые языки позволяют игнорировать множество проблем с типизацией, что обычно приводит к уменьшению объема кода, а вместе с объемом - и к сложности. Плюс обычно для подобных языков существуют специальные модули, позволяющие делать проверку типов входных данных. 

Так что невозможно ответить, какой из вариантов лучше. 

## Парадигмы

Парадигма программирования, в общем случае - это набор идей и понятий, определяющих подход к программированию. Условно говоря, парадигма описывает **какой должна быть программа - чем она и каким образом оперирует.** 

Парадигм существует огромное количество. Используемых в реальной разработке парадигм, к счастью, намного меньше. На них я и остановлюсь.

### Императивность VS Декларативность

Основная разница между императивными и декларативными языками заключается в одном простой детали, полностью изменяющей весь стиль программирования. Императивные языки (их большинство) описывают, **как** необходимо что-то сделать. Программист пишет ряд инструкций для машины, которые исполняются последовательно и приводят к какому-то результату. Декларативные же языки описывают, **что** нужно сделать. 

На практике учиться всегда проще, поэтому рассмотрим небольшую задачу. У нас есть таблица (массив) с данными пользователей какого-либо сайта. Нужно найти всех пользователей, возраст которых меньше 18.

Как это решается на императивном языке (к примеру, Python):
```python
for user in users_table:
    if user.age < 18:
        print(user)
```
Или, в переводе на более человеческий язык, `пробегись по всем пользователям в таблице и проверь их возраст, если возраст пользователя меньше 18 - выведи его на экран`

Как задача будет решаться на декларативном языке (SQL, язык запросов к базам данных):

```SQL
SELECT user FROM user_table WHERE user.age < 18;
```

Или, в переводе на человеческий, `а дерни-ка мне плиз из таблицы пользователей всех, у кого возраст меньше 18`.

Декларативные языки на данный момент - довольно редкая птица, так как весьма близки к математике (говорят, что программа на декларативном языке является формальной теорией, а ее исполнение является одновременно автоматическим доказательством этой теории. Что это значит, я примерно пониманю, но мой навык подбора метафор тут пробуксовывает). Самым популярным декларативным языком на данный момент является SQL, который исползуется для управления базами данных. И используется довльно ширкоко. 

### Структурное программирование
Уже описывалось в [предыдущей лекции](https://github.com/antonkravtsevich/beginners_programmers/blob/master/2_some_history.md#%D0%A1%D1%82%D1%80%D1%83%D0%BA%D1%82%D1%83%D1%80%D0%BD%D0%BE%D0%B5-%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5)

### Объектно-ориентированное программирование
[Та же фигня](https://github.com/antonkravtsevich/beginners_programmers/blob/master/2_some_history.md#%D0%9E%D0%B1%D1%8A%D0%B5%D0%BA%D1%82%D0%BD%D0%BE-%D0%BE%D1%80%D0%B8%D0%B5%D0%BD%D1%82%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%BD%D0%BE%D0%B5-%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5)

### Функциональное программирование

Функциональное программирование, если говорить начистоту, не совсем даже программирование, а скорее раздел дискретной математики. Вычисления в функциональных языках трактуются как вычисления значений функции в математическом понимании последних. То бишь функции в функциональных языках - это не подпрограммы, как в структурных. Функциональные языки обычно не заморачиваются такой вещью, как хранение состояния в переменных, и делают это, к примеру, в стеке вызова функции. Знаю, что вы еще пока с этими понятиями не знакомы, просто хочу пояснить, что функциональные языки - довольно таки стрёмный раздел (и почему-то они мне очень нравятся). Не смотря на свою относительную дикость, они нашли широкое применение в высоконагруженных системах, там, где программы должны быть **многопоточными**

Когда-нибудь я запилю отдельную часть по функциональным языкам, но на данный момент это не столь важный вопрос. 

## Вместо заключения

На этом нудная теория закончена. Обе эти статьи преследовали одну цель - дать вам некоторое представление о том, че происходит в океане языков программирования, перед тем как спихнуть вас туда головой вниз. Различия между языками программирования (а это далеко не все, я описал лишь те, которые обладают существенной важностью для старта обучения) помогут вам понять, с какого перепугу, к примеру, в Java нельзя объявлять переменные без типа, а в Python можно. 
В следующей главе мы наконец-то начнем прогать. Ура.