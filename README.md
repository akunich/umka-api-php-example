# umka-api-php-example
Пример работы с HTTP API Umka ККМ с использованием PHP

Внимание, класс изначально расчитан исключительно под генерацию бланков строгой отчётности (чеки БСО). Они используются при продаже услуг. Для продажи товаров нужно почитать документацию к ФФД (формату фискальных данных) и сменить шаблон генерации чека под продажу товаров. 
Документация ФФД: http://dev.umki.org/%D0%A4%D0%BE%D1%80%D0%BC%D0%B0%D1%82%D1%8B-%D1%84%D0%B8%D1%81%D0%BA%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D1%85-%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85.docx
Гораздо лаконичнее документация к умке (основное по ФФД там есть): http://umki-static.armax.ru/docs/%D0%9E%D0%BF%D0%B8%D1%81%D0%B0%D0%BD%D0%B8%D0%B5%20%D0%B2%D1%8B%D1%81%D0%BE%D0%BA%D0%BE%D1%83%D1%80%D0%BE%D0%B2%D0%BD%D0%B5%D0%B2%D0%BE%D0%B3%D0%BE%20API%20%D0%9C%D0%95%D0%A9%D0%95%D0%A0%D0%90-%D0%A3%D0%9C%D0%9A%D0%90.pdf

Пример отправки чека приведён в test.php
Перед отправкой вызывается метод init() , который проверяет статус открытия смены. Если смена не открыта, открывает её. Сказать честно, тут бы пересмотреть немного логику. Возможно, логичнее вставить открытие смены в непосредственно метод печати чека - fiscalcheck($invoice, $positions).

Чтобы посмотреть структуру ожидаемых массивов, передаваемых при печате чека, в примере сохранены сериализованные массивы с входными данными, которые использовались при тестировании класса (см. код test.php )