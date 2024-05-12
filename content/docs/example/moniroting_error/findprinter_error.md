---
weight: 3
title: "Обнаружены не все печатающие устройства"
--- 

# Обнаружены не все печатающие устройства

* Проверьте, что IP-адрес принтера указан верно в настройках локации или входит в указанные диапазоны. 

    Для этого откройте панель администратора мониторинга, выберите Инвентаризация > Локации. Откройте нужную локацию и убедитесь, что нужный IP-адрес указан в поле “IP-адреса устройств” и не указан в поле “Исключить IP-адреса”.

* Проверьте, что агент мониторинга опрашивает локацию с устройствами. 
    Для этого перейдите во вкладку “Настройки” > “Общие настройки” > “Модули” и выберите вариант “Сетевой агент”.  

    Локация с устройствами должна быть отмечена чек-боксом или входить в другую локацию, отмеченную чек-боксом. 

* Проверьте доступность принтера по его ip-адресу в сети. 
    Для этого на ПК, находящемся в одной сети с принтером, откройте браузер и укажите в адресной строке ip-адрес принтера. 

* Если принтер отвечает по указанному в настройках локации ip-адресу, проверьте, включена ли на принтере передача данных по протоколу SNMP. 

    Если нет, необходимо включить.

    Проверьте, отвечают ли принтеры на запросы и отдают ли информацию по snmpwalk по командам:

        snmpwalk -v 2c -c public printer-ip-address

    или 

        snmpwalk -v 1 -c public printer-ip-address


    Если принтеры не отвечают на команды, следует откорректировать настройки принтеров и включить передачу данных по протоколу SNMP.

* Если нужный ip-адрес указан в настройках локаций, принтер по нему отвечает и в настройках включена передача данных по протоколу SNMP, вероятно, потребуется настройка SNMP параметров для данной модели. Сделайте необходимые настройки или обратитесь в техническую поддержку. 

    При обращении в техподдержку в запросе также укажите ошибки идентификации по этому устройству. Чтобы их посмотреть, перейдите в “Инвентаризация” > “Устройства”, найдите нужное устройство, вбив ip-адрес в строку поиска, скопируйте данные из столбца “Ошибки идентификации”.

* Для случаев, когда устройств много и необходимо проверить на каких включена или выключена передача данных по SNMP есть консольная приложение printer.py. Инструкция по его использованию в разделе “Приложение printer.py для поиска устройств”.  