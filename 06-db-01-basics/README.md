Задача 1

Архитектор ПО решил проконсультироваться у вас, какой тип БД лучше выбрать для хранения определенных данных.  

Он вам предоставил следующие типы сущностей, которые нужно будет хранить в БД:  

    Электронные чеки в json виде  
    Склады и автомобильные дороги для логистической компании  
    Генеалогические деревья  
    Кэш идентификаторов клиентов с ограниченным временем жизни для движка аутенфикации  
    Отношения клиент-покупка для интернет-магазина  

Выберите подходящие типы СУБД для каждой сущности и объясните свой выбор.  

Ответ:  

1. Электронные чеки в json виде: Документоориентированная БД (например MongoDB).  
JSON файл состоит из наборов ключ-значение, это хорошо подходит для  
документоориентированной БД.  
2. Склады и автомобильные дороги для логистической компании: Графовая БД.  
Узлы будут складами. Ребра допустим расстоянием между ними.  
3. Генеалогические деревья: Иерархическая БД. Древовидная структура отлично  
подходит для постороения генеалогического дерева.  
4. Кэш идентификаторов клиентов с ограниченным временем жизни для движка аутенфикации:  
Ключ-значение( например Redis). Тут нужен только клиент и его токен.  
5. Отношения клиент-покупка для интернет-магазина: Реляционная БД. Множество  
различных связанных значений (хар-ки товаров и т.д., варианты оплаты, доставка)  

---

Задача 2  

Вы создали распределенное высоконагруженное приложение и хотите классифицировать его согласно CAP-теореме.  
Какой классификации по CAP-теореме соответствует ваша система, если (каждый пункт - это отдельная  
реализация вашей системы и для каждого пункта надо привести классификацию):  

    Данные записываются на все узлы с задержкой до часа (асинхронная запись)  
    При сетевых сбоях, система может разделиться на 2 раздельных кластера  
    Система может не прислать корректный ответ или сбросить соединение  

А согласно PACELC-теореме, как бы вы классифицировали данные реализации?  

Ответ:  

1. Данные записываются на все узлы с задержкой до часа (асинхронная запись) - AP  
2. При сетевых сбоях, система может разделиться на 2 раздельных кластера. - PC  
3. Система может не прислать корректный ответ или сбросить соединение. - CP  

А согласно PACELC-теореме, как бы вы классифицировали данные реализации?  

1. PC/EC  
2. PA/EL  
3. PC/EC  

---

Задача 3  

Могут ли в одной системе сочетаться принципы BASE и ACID? Почему?  
Ответ:  
Не могут, т.к. противоречат друг другу.  

---

Задача 4  

Вам дали задачу написать системное решение, основой которого бы послужили:  

    фиксация некоторых значений с временем жизни  
    реакция на истечение таймаута  

Вы слышали о key-value хранилище, которое имеет механизм Pub/Sub. Что это за система? Какие   
минусы выбора данной системы?  

Ответ:  
На примере Redis: Pub/Sub - возможность подписаться на канал и получать сообщения из него,  
или отправлять в этот канал сообщение, которое будет получено всеми подписчиками  
Недостатки: Механизм pub/sub не гарантирует доставки сообщений, не гарантирует консистентности.  