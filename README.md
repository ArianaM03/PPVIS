# PPVIS
## Описание объектной модели банкомата
### Текстовое описание программы: 
**Банкомат** - аппарат для выдачи и приема денег, а также оплаты услуг и погашения кредитов без участия сотрудника банка, с использованием банковских карт.
Простым языком банкомат это некий компьютер с подключенной периферией, менеджером оборудования и банковским приложением, управляющим всем этим. Все решения по выдаче денег принимает сервер. Банкомат лишь собирает информацию от клиента и передает ее на сервер.
Простейшая модель банкомата включает в себя:
- картридер для чтения карты клиента
- пин-пад для ввода пин-кода и прочей информации как, например, суммы платежа/снятия
- панель с тремя активными кнопками: enter (ввод), cancel (отмена), correction(коррекция)
- диспенсер для выдачи денег
- различные датчики, подсветка, видеокамера и тд

**Принцип работы:**

Первая стадия “взаимодействия” с банкоматом – ввод карты в считывающий модуль (картридер). Затем указание пин-кода для авторизации пользователя. На ввод пин-кода дается три попытки, а обратном случае карта владельца блокируется. Далее происходит определение нужной операции, подтверждающийся нажатием кнопки “enter”:
- снятие наличных с банковской карты
- пополнение банковской карты путем ввода наличных
- запрос баланса банковской карты 
- выписка по последним операциям с участием данной банковской карты 
- перевод средств с карты на карту

После выбора операции происходит повторный запрос пин-кода, так же три попытки. После выбора операции банкомат шифрует полученную информацию (содержимое магнитной полосы/чипа, введенный ПИН-код, запрошенную операцию) и передает данные в центр обработки банка-эквайера (который обслуживает данный банкомат).  Далее выполняются следующие операции:
- запрос от банка в платежную систему
- отправление запроса в банк, выпустивший пластиковую карту
- получение одобрения или отказа в проведении операции
- передача ответа на банкомат

Выдача наличных выполняется из кассет, в устройстве их несколько, в каждой размещены купюры конкретного номинала, что исключает ошибку в суммах. При приеме наличности от клиента проводится анализ купюры по восьми признакам, так что устройство вряд ли примет фальшивку.
Рассмотрим принцип работы каждой из операций:
1. Снятие наличных с банковской карты                                                                                     
При выборе данной операции первый делом запрашивается пин-код для подтверждения владельца. Затем при верном вводе пин-кода пользователю предоставляется возможность увидеть баланс на своей карте и в этом же окне вписать какую сумму он хочет снять. При нажатии кнопки “enter” пользователь может выбрать каким номиналом купюры он хочет видеть либо же выбрать вариант любыми. Происходит повторный ввод пин-кода, и при его правильном введении через диспенсер для выдачи денег пользователь может забрать их. В конце операции пользователь может напечатать либо же отказаться от бумажного чека, а затем выходит обратно на главное меню.
2. Пополнение банковской карты путем ввода наличных                                                                       
При выборе данной операции первый делом запрашивается пин-код для подтверждения владельца. Затем при верном вводе пин-кода пользователю предоставляется возможность увидеть баланс на своей карте и в этом же окне можно вписать на какую сумму пользователь хочет пополнить баланс. Далее пользователь вводит по одной купюре через специальный диспенсер. После проверки каждой купюры на подлинность высвечивается уведомление о том прошла ли данная операция успешно. Если да, то пользователю показывается обновленный баланс его карты и он может выйти обратно в меню. В противном случае банкомат возвращает неодобренные купюры и просит их заменить.
3. Запрос баланса банковской карты                                                                                                                         
При выборе данной операции пользователь может просмотреть баланс банковской карты без дополнительного ввода пин-кода. После чего возвращается обратно на главное меню.
4. Выписка по последним операциям с участием данной банковской карты  
При выборе данной операции пользователь может запросить выписку за определенный промежуток времени (максимум до года), которая пришлется на номер телефона, который он введет. 
5. Перевод средств с карты на карту                                             
При выборе данной операции первый делом запрашивается пин-код для подтверждения владельца. Затем при верном вводе пин-кода пользователю предоставляется возможность увидеть баланс на своей карте. Дальше ему надо будет заполнить поля о карте, на которую он хочет сделать перевод средств. В самом конце пользователю надо будет ввести сумму, которую он хотел бы перевести. При условии, что данная сумма есть на его счете, происходит повторный ввод пин-кода. Если нет, то пользователь получит об этом уведомление и ему представится возможность еще одна попытка ввести сумму, которую он хочет перевести. В конце операции пользователь может увидеть обновленные сведения баланса банковской карты и вернуться на главное меню.

**Описание через пользовательские истории:**
- как пользователь банкомата, я хочу увидеть баланс на своей карте
- как пользователь банкомата, я хочу иметь возможность перевода денег на другую карту
- как пользователь банкомата, я хочу иметь - возможность выбора номинала купюр при снятии денег с карты
- как пользователь банкомата, я хочу иметь возможность отказаться от физического чека 
- как пользователь банкомата, я хочу видеть баланс своего банковского счета до транзакции

**Направления развития:**
- Добавления возможности оплаты коммунальных услуг 
- Добавление печати истории карты 
- Добавление функции отключения банковской карты

**ER-диаграмма модели банкоматa**

![er diagram](https://github.com/ArianaM03/PPVIS/blob/main/doc/erDiagram.png)

**BPMN-диаграмма модели банкоматa**
![bpmn diagram](https://github.com/ArianaM03/PPVIS/blob/main/doc/bpmnDiagram.png)

**Use case диаграмма модели банкомата**
![use case diagram](https://github.com/ArianaM03/PPVIS/blob/main/doc/useCase.png)

**Sequence диаграмма модели банкомата**
![sequence diagram](https://github.com/ArianaM03/PPVIS/blob/main/doc/sequenceqDiagram.png)

**Базовая диаграмма классов модели банкомата**
![class diagram base](https://github.com/ArianaM03/PPVIS/blob/main/doc/classDiagramBase.png)

**Диаграммы классов исходя из направлений развития**
1. Оплата коммунальных услуг
![first](https://github.com/ArianaM03/PPVIS/blob/main/doc/classDiagram1.png)

2. Функция отключения карты
![second](https://github.com/ArianaM03/PPVIS/blob/main/doc/classDiagram2.png)

3. Печать истории банковской карты
![third](https://github.com/ArianaM03/PPVIS/blob/main/doc/classDiagram3.png)

**Интерфейс**
![interface](https://github.com/ArianaM03/PPVIS/blob/main/doc/interface.jpg)
