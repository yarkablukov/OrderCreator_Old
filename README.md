# OrderCreator
Тестовый .NET проект содержится в архиве OrderCreator.
Приложение загружает xml файлы-заказы клиентов, валидирует их по xsd-схеме и на их основании создает xml файлы-ордера на доставку.
После этого доступно несколько вариантов отчетов на основании загруженных заказов.
Перед запуском приложения необходимо настроить локальные пути определения папок с заказами, ордерами загрузки, xsd-схемой и логами (см. ниже).

Порядок работы приложения при запуске:

1. Проход по всем xml-файлам заказов клиентов:

1.1.	Определение локального пути, в котором лежат xml-файлы заказов клиентов для загрузки. Путь указывается в Program/customerOrdersDirectory.

1.2. Валидация по xsd-схеме. Путь к схеме указывается в Program/xsdSchemaPath.

1.3. Загрузка данных из xml-файла с помощью класса CustomerOrderLoader, создание экземпляра класса CustomerOrder, вывод в консоль данных о спецификации загруженного заказа.

1.4. Логирование факта загрузки заказа в файл по пути CustomerOrderLoader/writePath.

1.5. Создание ордера на доставку на основании заказа с помощью классов DeliveryOrderUnloader и DeliveryOrder.

1.6. Выгрузка сформированного xml ордера на доставку в папку по пути Program/deliveryOrdersDirectory.

1.7. Логирование факта сформированного ордера на доставку по пути DeliveryOrderUnloader/writePath.

1.8. Добавление заказа клиента в коллекцию statisticsDocuments для дальнейшего использования в статистических отчетах.

2. Предоставление статистики по загруженным заказам до момента выхода из приложения.

Примечания:
- Отчеты со статистикой формируются методом LINQ To XML по всем заказам клиентов из папки customerOrdersDirectory
- Реализована простая валидация по xsd-схеме. За "отлов" ошибок валидации отвечает метод Program/ValidationEventHandler

Возможные пути развития приложения
- Улучшить валидацию данных по xsd схеме - например, добавить проверку на непустоту string значений.
- Реализовать сохранение данных в БД.
- Вынести настройки локальных путей куда-то в единое место для удобной настройки.
