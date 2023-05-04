# IST
Interview Sovcombank Technologies

Проект прохождения интервью с автоматизированным сбором результатов и доставкой до сотрудника принимающего решение о дальнейшейм найме.

Стек: Python,SQL Lite.
Фреймворк: Django.
IDE: Visual Studio Code.
Бекенд: Raspberry Pi 4, Ubuntu

Флоу работы:

Проведение собеседования:
- Первый пользователь из комиссии под УЗ "Пользователь" выбирает сгенерировать новую сессию собеседования и создает уникальный идентификатор в виде ID.
- Заполняет карточку соискателя професии (ФИО, контактные данные обязательное поле Email, файл резюме в формате PDF, прикладывает ссылку на комнату в Skype, контакты HR специалиста EMAIL, telegramm_ID)
- Остальные сотрудники используя УЗ "Пользователь" подключаются по расшаренному ID к общей сессии собеседования.
- Все авторизованные УЗ у которых есть ID сессии получают список выбранных тем из БД (отображаем в виде списка с чек боксами).
- Когда УЗ "Пользователь" выставляет свой чек бокс всегда отправляем данные на сохраннение в таблицу сохраняющей в себе данные по сессии, user ID и темы закрепленные за каждым пользователем в этой сессии.
- Если мы наблюдаем что за одной темой закрепились несколько пользователей просим переголосовать с указанием того какие ID пользовательей конфликтуют между собой и по каким темам.
- После того как все темы будут закреплены за уникальным User ID бех конфликтов, пользователям будет доступна кнопка начала проведения собеседования.
- В начале отображается приветственная часть с описанием формата проведения собеседования для соискателя ведущий создавший сессию собеседования озвучивает вступительную речь и по нажатию кнопки старт передает кнопку.
- Отображаем на странице с вопросами по теме ID ведущего который будет задавать вопрос и первый вопрос из списка сохраненных в бекенде (можно в рандомном порядке) с ответом (берем из БД так же).
- Отображаем таймер оставшегося времени на данную тему (блок вопросов) и отсчитываем время до старта следующего ведущего и тему его вопросов. Предоставляем кнопки перехода от одного вопроса к другому с формой оценки.
- Когда таймер заканчивается кнопки у предыдущего User ID забираем и передаем следующему пользователю.
- Пользователь который уже задал свои ответы получает список озвученных им вопросов и пишет по ним обратную связь на соответствующей странице. По кнопке отправить сохраняем данные в БД.
- После блока вопросов у последнего "Пользователя" и истечении времени передаем слово ведущему и отображаем ему страницу с регламентом проведения оставшейся части.
- При завершении нажимаем кнопку "Собеседование окончено" и сохраняем в таблице с результатами по session id оценку по всем пользователям написавших ответы
- В беке как только по данному session ID все пользователи заполнят резултьтаты - отправляем руководителю в личный кабинет (Админу) данные по session ID и форму ввода итогового результата по кандидату.
- Руководитель указывает команду в которую он предполагает направить данного кандидата при успешном прохождении собеседования.
- Руководитель указывает результаты при неуспешном прохождении интервью
- Результаты направляются на email HR специалиста и в телеграмм для дальнейшего общения с кандидатом.

Статистика:
- Выводим статистику за неделю о успешном найминге и в какие команды
- Выводим статистику о неуспешном найминге


Роли:
Админка (сохранение вопросов по темам с привязкой по ID, удаление старых вопросов по ID)
Пользователь (проведение интервью 

Модули:
Авторизация
Генрация токена и проверка его с клиентом
Страницы под соответствующие роли (состаав уточняется)
Сущности БД(состав формируется)
Модуль отправки в телеграмм сообщений для HR
Модуль для отправки SMTP писем для HR
Арбитр (порядка проведения собеседования)
Арбитр (порядка выбора тем за пользователям)


Создаваемые сощности.
Table Name:
Query List.
User list
Admin list
Sesson list
Resume
(дальнейший список на уточнении)
