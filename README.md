# Marlin-Erzay3D
Прошивка <b>Marlin 1.1.9</b> для принтеров <b>Erzay3D</b>

<img src="https://github.com/Robokinetics/Marlin-Erzay3D/blob/master/logo.png"/>

Оригинальная прошивка: https://github.com/MarlinFirmware/Marlin

## Основные особенности:
* Конфигурация для <b>Delta</b>;
* Рускоязычный интерфейс с небольшими исправлениями перевода;
* Поддержка <b>SD-карт</b>;
* Поддержка <b>UBL</b> (Унифицированное выравнивание стола);
* Поддержка команды <b>G26</b> для печати калибровочной сетки;
* Поддержка команды <b>G33</b> для калибровки Delta-принтера;
* "Продвинутая пауза" - парковка печатающей головки во время паузы + возможность смены филамента;
* Функция смены, загрузки и выгрузки филамента;
* Активированный <b>SPEAKER</b> (бипер, пищалка), поддержка команды <b>M300</b>;
* Увеличенный диапазон допустимых температур печати для уменьшения вероятности ложного срабатывания защиты от теплоубегания;
* Фирменное окно приветствия;
* Отключено опускание печатающей головки по завершении операции <b>Homing</b> для предотвращения повреждения высоких напечатанных моделей;
* Активировано дополнительное меню <b>"Быстрые команды"</b> (Изменённое название "Свои команды"). Содержит в себе 5 функций:
    1) Домой (G28);
    2) Преднагрев PLA;
    3) Преднагрев ABS;
    4) Автокалибровка стола (G28\nG29 P1\nG29 T0\nG29 S-1\nG29 A\nM500);
	5) Полная автокалибровка (G28\nM502\nM500\nG33\nM500\nG29 P1\nG29 T0\nG29 S-1\nG29 A\nM500).
* Использоване EEPROM для хранения настроек;
* Увеличено время активности шаговых двигателей до двух часов с момента последнего движения;
* Плата BOARD_MKS_GEN_13, дисплей MKS_MINI_12864;
* Добавлена информация о серийном номере принтера;
* И прочее.


## Инструкция по установке для пинтеров Erzay3D
### Внимание! Убедитесь, что Вы имеете работающую прошивку сконфигурированную под Ваш принтер. В противном случае, при неправильной конфигурации прошивки может потребоваться помощь специалиста
1. Скачайте и распакуйте архив исходного кода прошивки;
2. Скачайте и установите <b>Arduino IDE</b>: https://www.arduino.cc/en/main/software
3. Запустите Arduino IDE</b> и откройте через него файл <b>Marlin/Marlin.ino</b>;
4. Откройте вкладку <b>Configuration.h</b> и укажите серийный номер Вашего принтера, если он Вам известен в строке <b>#define SERIAL_NUMBER "XX-YYYY"</b>, где XX-YYYY - серийный номер;
5. Во вкладке "Configuration.h" найдите строку, начинающуюся с <b>#define MACHINE_UUID</b> и укажите в кавычках UUID Вашего принтера, если он известен;
6. В строке <b>#define DELTA_PRINTABLE_RADIUS 100.0</b> укажите радиус области печати в мм, в строке <b>#define DELTA_DIAGONAL_ROD 320.0</b> укажите длину тяговых в мм;
7. Сделайте прочие изменения в файла <b>Configuration.h</b> и <b>Configuration_adv.h</b>, если необходимо;
8. В меню <b>Инструменты->Плата</b> выберите плату, установленную на Вашем принтере (обычно это <b>Arduino/Genuino Mega or Mega2560</b>)
9. В меню <b>Инструменты->Процессор</b> выберите процессор, установленный на Вашем принтере (обычно это <b>ATmega2560 (Mega2560)</b>);
10. В меню <b>Инструменты->Программатор</b> выберите программатор, установленный на плате Вашего принтера (обычно это <b>AVR ISP</b>);
11. Для поддержки графических дисплеев добавьте библиотеку <b>U8glib</b>, если ранее Вы этого не делали: скачайте zip-архив библиотеки из репозитория: https://github.com/olikraus/U8glib_Arduino или по ссылке: https://bintray.com/olikraus/u8glib/Arduino. Зайдите в меню <b>Скетч->Подключить библиотеку->Добавить .ZIP библиотеку...</b>;
Для владельцев oled-дисплеев:
	1. В файле <b>Configuration.h</b> закомментируйте строчку <b>#define MKS_MINI_12864</b>;
	2. ...
12. Установите драйвер Вашего принтера, если ранее он не был установлен;
13. Подключите Ваш принтер по USB порту, в меню <b>Инструменты->Порт</b> выберите порт Вашего принтера;
14. Убедитесь, что порт Вашего принтера не занят другими программа. Некоторые программы (например, <b>Cura</b> версии 3 и выше) занимают порт принтера, как только он будет подключен к ПК. Поэтому рекомендуется закрыть подобные программы;
15. Нажмите кнопку <b>Загрузить</b> в окне Arduino IDE;
16. Дождитесь загрузки прошивки на Ваш принтер. После удачной загрузки на дисплее должен появиться логотип и окно статуса;
17. Подключите принтер к сети питания, выполните операцию "Домой" из меню "Быстрые команды". При этом следите, чтобы все направляющие поднимались вверх и срабатывали концевики. <b>БУДЬТЕ ГОТОВЫ (!)</b> отключить питание, в случае неправильной работы . Если одна или более направляющих опускаются вниз, отключите питание, в файле <b>Configuration.h</b> поменяйте значение (<b>true</b> на <b>false</b>, а <b>false</b> на <b>true</b>) у <b>INVERT_X_DIR</b>, <b>INVERT_Y_DIR</b> или <b>INVERT_Z_DIR</b>, соответственно для каждого шагового двигателя, который двигается в противоположную от нужной сторону. После изменения повторите шаги 14-16;
18. Убедитесь, что датчик калибровки стола исправен и подключен к Вашему принтеру. Подготовьте стол, как если бы Вы собрались на нём печатать. В меню дисплея Вашего принтера откройте раздел <b>Быстрые команды</b>, и выберите <b>Полная автокалибровка</b>. Дождитесь, пока принтер выполнит калибровку. При этом следите, чтобы зонд не выходил за пределы стола. Все откалиброванные параметры сохранятся в EEPROM (энергонезависимая память) принтера;
19. Проверьте направление вращения шагового двигателя экструдера(ов) с помощью хост-программы или дисплея принтера, при этом нагрев экструдер до необходимой температуры печати. Если он движется в противоположную сторону поменяйте параметр <b>INVERT_E0_DIR</b> (<b>true</b> на <b>false</b>, а <b>false</b> на <b>true</b>) в файле <b>Configuration.h</b> и загрузите прошивку в принтер заново. Для многоэкструдерного принтера настройте параметры <b>INVERT_E0_DIR</b>, <b>INVERT_E1_DIR</b>, <b>INVERT_E2_DIR</b> и т.д. соответственно для каждого экструдера;
20. Чтобы проверить качества калибровки используйте команду <b>G26 Bxx Hyy</b>, где <b>B</b> - это температура нагрева стола (для PLA = 60, для ABS = 95), <b>H</b> - температура нагрева экструдера (для PLA = 210, для ABS = 240). Принтер начинает нагреваться до указанных температур и печатает тестовую сетку. Подробнее о калибровке читайте: http://3dtoday.ru/blogs/otumanov/ubl-or-how-to-get-a-perfect-first-layer/
21. <b>Принтер готов к работе</b>.

Подробнее о настройке прошивки для Delta-принтера: http://3dtoday.ru/blogs/xolodny/preparation-and-marlin-firmware-for-delta-printer/



