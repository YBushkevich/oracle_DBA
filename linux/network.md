# Сети в операционной системе UNIX

Архитектура семейтва протоколов TCP/IP основана на представлении, что
комуникационная инфраструктура включает три объекта: процессы, хосты, и сети.
Процесыы являются основными коммуникационными объектами, поскольку между
процессами, в конечном итоге, осуществляется передача информации. Выполнение
процессов происходит на различных хостах (или компьютерах). Передача информации
между процессами проходит через сети, к которым подключены хосты.

Модель OSI

7. Прикладной (application) — доступ к сетевым службам.(Данные)
6. Уровеь представления (presentation) — представление и шифрование данных.
(Данные)
5. Сеансовый (session)  — управление сеансом связи.
4. Транспортный (transport) — прямая связь между конечными пунктами и
надежность.(Сегменты)
3. Сетевой (network) — определение маршрута и логическая адресация.
(Пакеты/датаграммы)
2. Канальный (data link) — физическая адресация.(Кадры)
1. Физический (physical) — работа со средой передачи, сигналами и двоичными
данными.(Биты)

Заметки:

5. Сеансовый — задача данного уровня организовать сеансы обмена между конечными
машинами. Обычно протоколы этого уровня являются составной частью функции трех
верхних уровней OSI.
Пример. При организации аудио- и видеоконференции именно на данном уровне
устанвливается,  каким кодеком сиграл будет кодироваться. При этом данный кодек
должен быть на обоих устройствах. 
6. Уровень представления (presentation) — данный уровень отвечает за возможность
диалога между приложениями на различных машинах. Им обеспечивается
преобразование (кодирование, компрессия) данных прикладного уровня в поток
данных для транспортного уровня. Обычно протоколы уровня представления являются
составной частью функции трех верхних уровней OSI.
Пример. Видимые вами на экране изображения (картинки) при пересылке файла
передаются маленькими порциями единиц и ноликов (битов). Когда вы посредством
электронной почти пересылаете другу фотографию, протокол прикладного уровная
(для передачи-приема почты это SMPT) отправляет данное фото на нижний уровень,
то есть на уровень представления. На нем происходит преобразование фотографии в
вид, удобный для более низких уровней, к примеру в биты (1 и 0). Точно так же
как ваш друг будет получать высланное фото в виде 1 и 0, и именно на уровне
представления произойдет преобразование их в полноценную фотографию, например
JPEG.
7. Прикладной — отвечает за доступ (осуществляет связь) приложений в сеть.
Задача прикладного уровня: перенос файлов, обмен почтовыми сообщениями и
управление сетью.

## 1

Сетевые элементы, осуществляющие передачу данных из одной сети в другую,
получили навазвание **шлюзов** (gateaway). Более точным названием этих устройств
является **"маршрутизатор" (router)**. Шлюз имеет несколько сетевых интерфейсов,
подключенных к различным физическим сетям, и его основной задачей является выбор
маршрута передачи данных из одного сетевого интерфейса в другой.

Для правильного обмена даннымм каждый коммуникационный узел должен иметь
уникальный адрес. Существует несколько уровней адресации. В локальной сети,
каждый сетевой интерфейс (первый уровень модели) имеет т.н. **MAC-адрес**. С
помощью этого адреса обеспечивается доставка данных требуемому получателю в
физической сети.

Поскольку путь данных может проходить по нескольким физическим сегментам,
физический адрес, или MAC-адрес, сетевого интерфейса не имеет смысла и
определяется автоматически на каждом этапе пересылки (hop) между шлюзами.

IP выполняет три основные функции: адресацию, фрагментацию, и маршрутизацию
данных. 
Датаграмма — обычно используется для описания пакета данных, передаваемого по
сети без установления предварительной связи.
В процессе обработки датаграммы протокол IP иногда вынужден выполнять ее
**фрагментацию**. Фрагментация бывает необходима, поскольку путь датаграммы от
источника к получателю может пролегать через локальные и
территориально-распределенные физические сети различной топологи и архитектуры,
использующие различный размер кадра.

Адрес сетевого адаптера определяет расположение хоста в физической сети.

## Классы адресов

Для определения фактической границы между адресом подсети и хоста используется
**маска подсети**.















