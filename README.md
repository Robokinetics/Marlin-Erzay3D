# Marlin-Erzay3D
Прошивка <b>Marlin 1.1.9</b> для принтеров <b>Erzay3D</b>

<img src="https://github.com/Robokinetics/Marlin-Erzay3D/blob/master/logo.png"/>

* Репозиторий оригинальной прошивки: https://github.com/MarlinFirmware/Marlin
* Сайт разработчиков Marlin: http://marlinfw.org
* Документация по командам Marlin: http://marlinfw.org/meta/gcode/

## Основные особенности:
* Конфигурация <b>Delta</b>-кинематики 3D-принтера;
* Рускоязычный интерфейс с исправлениями перевода;
* Поддержка <b>SD-карт</b>;
* Поддержка <b>UBL</b> (Унифицированное выравнивание стола);
* Поддержка команды <b>G26</b> для печати калибровочной сетки;
* Поддержка команды <b>G33</b> для калибровки Delta-принтера;
* <b>Продвинутая пауза</b> - парковка печатающей головки во время паузы;
* Функция смены, загрузки и выгрузки филамента;
* Активированный <b>SPEAKER</b> (бипер, пищалка), поддержка команды <b>M300</b> (Только для принтеров Erzay3D <b>2017</B> года выпуска и позднее);
* Увеличенный диапазон допустимых температур печати для уменьшения вероятности ложного срабатывания защиты от теплоубегания;
* Фирменное окно приветствия;
* Отключено опускание печатающей головки по завершении операции <b>Homing</b> для предотвращения повреждения высоких напечатанных моделей;
* Активировано дополнительное меню <b>Быстрые команды</b>. Содержит в себе 5 функций:
    1) Домой (G28);
    2) Преднагрев PLA;
    3) Преднагрев ABS;
    4) Автокалибровка стола (G28\nG29 P1\nG29 T0\nG29 S-1\nG29 A\nM500);
    5) Полная автокалибровка (G28\nM502\nM500\nG33\nM500\nG29 P1\nG29 T0\nG29 S-1\nG29 A\nM500).
* Использоване <b>EEPROM</b> для хранения параметров и настроек принтера;
* Увеличено время активности шаговых двигателей до двух часов с момента последнего движения;
* Добавлена информация о серийном номере принтера;
* Другие изменения.


## Инструкция по установке для пинтеров Erzay3D
### Внимание! Убедитесь, что Вы имеете работающую прошивку сконфигурированную под Ваш принтер. В противном случае, при неправильной конфигурации прошивки может потребоваться помощь специалиста
1. Скачайте и распакуйте архив исходного кода прошивки;
2. Для принтеров <b>Erzay3D</b> <b>2016</b> года выпуска и ранее: зайдите в папку с прошивкой, скопируйте все файлы из папки <b>Marlin/example_configurations/Erzay3D2016</b> в папку <b>Marlin</b> с заменой файлов;
3. Скачайте и установите <b>Arduino IDE</b>: https://www.arduino.cc/en/main/software
4. Запустите <b>Arduino IDE</b> и откройте через него файл <b>Marlin/Marlin.ino</b>;
5. Откройте вкладку <b>Configuration.h</b> и укажите серийный номер Вашего принтера, если он Вам известен в строке <b>#define SERIAL_NUMBER "XX-YYYY"</b>, где <b>XX-YYYY</b> - серийный номер;
6. Во вкладке <b>Configuration.h</b> найдите строку, начинающуюся с <b>#define MACHINE_UUID</b> и укажите в кавычках UUID Вашего принтера, если он известен;
7. В строке <b>#define DELTA_PRINTABLE_RADIUS 100.0</b> укажите радиус области печати в мм (обычно это <b>100.0</b>), в строке <b>#define DELTA_DIAGONAL_ROD 320.0</b> укажите длину тяговых в мм (обычно это <b>320.0</b>);
8. Сделайте прочие изменения в файла <b>Configuration.h</b> и <b>Configuration_adv.h</b>, если необходимо. Подробнее читайте: http://marlinfw.org/docs/configuration/configuration.html или https://3dtoday.ru/blogs/akdzg/custom-firmware-marlin-and-pour-it-into-a-3d-printer/;
9. В меню <b>Инструменты->Плата</b> выберите плату, установленную на Вашем принтере (обычно это <b>Arduino/Genuino Mega or Mega2560</b>)
10. В меню <b>Инструменты->Процессор</b> выберите процессор, установленный на Вашем принтере (обычно это <b>ATmega2560 (Mega2560)</b>);
11. В меню <b>Инструменты->Программатор</b> выберите программатор, установленный на плате Вашего принтера (обычно это <b>AVR ISP</b>);
12. Для поддержки графических дисплеев добавьте библиотеку <b>U8glib</b>, если ранее Вы этого не делали: скачайте zip-архив библиотеки из репозитория: https://github.com/olikraus/U8glib_Arduino или по ссылке: https://bintray.com/olikraus/u8glib/Arduino. Зайдите в меню <b>Скетч->Подключить библиотеку->Добавить .ZIP библиотеку...</b> и выберите файл архива библиотеки;
13. Установите драйвер Вашего принтера, если ранее он не был установлен;
14. Подключите Ваш принтер по USB порту, в меню <b>Инструменты->Порт</b> выберите порт Вашего принтера;
15. Убедитесь, что порт Вашего принтера не занят другими программа. Некоторые программы (например, <b>Ultimaker Cura</b> версии 3 и выше) занимают порт принтера, как только он будет подключен к ПК. Поэтому рекомендуется закрыть подобные программы;
16. Нажмите кнопку <b>Загрузить</b> в окне <b>Arduino IDE</b>;
17. Дождитесь загрузки прошивки на Ваш принтер. После удачной загрузки на дисплее должен появиться логотип и окно статуса;
18. Подключите принтер к сети питания, выполните операцию <b>Домой</b> из меню <b>Быстрые команды</b>. При этом следите, чтобы все направляющие поднимались вверх и срабатывали концевики. <b>БУДЬТЕ ГОТОВЫ (!)</b> отключить питание, в случае неправильной работы . Если одна или более направляющих опускаются вниз, отключите питание, в файле <b>Configuration.h</b> поменяйте значение (<b>true</b> на <b>false</b>, а <b>false</b> на <b>true</b>) у <b>INVERT_X_DIR</b>, <b>INVERT_Y_DIR</b> или <b>INVERT_Z_DIR</b>, соответственно для каждого шагового двигателя, который двигается в противоположную от нужной сторону. После изменения повторите шаги <b>14-16</b>;
19. Убедитесь, что датчик калибровки стола исправен и подключен к Вашему принтеру. Подготовьте стол, как если бы Вы собрались на нём печатать. В меню дисплея Вашего принтера откройте раздел <b>Быстрые команды</b>, и выберите <b>Полная автокалибровка</b>. Дождитесь, пока принтер выполнит калибровку. При этом следите, чтобы зонд не выходил за пределы стола. Если зонд пытается выйти за пределы стола, то в файле <b>Configuration.h</b> уменьшите значение в строке <b>#define DELTA_PRINTABLE_RADIUS</b>, перепрошейте и выполните <b>Полную автокалибровку</b> заново. Все откалиброванные параметры сохранятся в энергонезависимой памяти принтера (EEPROM). <b>Примечание:</b> у принтеров Erzay3D 2016 года производства и ранее рекомендуется значение в строке <b>#define DELTA_PRINTABLE_RADIUS</b> устанавливать не более <b>80.0</b>;
20. Проверьте направление вращения шагового двигателя экструдера(ов) с помощью хост-программы или дисплея принтера, при этом нагрев экструдер до необходимой температуры печати. Если он движется в противоположную сторону поменяйте параметр <b>INVERT_E0_DIR</b> (<b>true</b> на <b>false</b>, а <b>false</b> на <b>true</b>) в файле <b>Configuration.h</b> и загрузите прошивку в принтер заново. Для многоэкструдерного принтера настройте параметры <b>INVERT_E0_DIR</b>, <b>INVERT_E1_DIR</b>, <b>INVERT_E2_DIR</b> и т.д. соответственно для каждого экструдера;
21. Чтобы проверить качества калибровки используйте команду <b>G26 Bxx Hyy</b>, где <b>B</b> - это температура нагрева стола (для PLA = 60, для ABS = 95), <b>H</b> - температура нагрева экструдера (для PLA = 220, для ABS = 240). Принтер начинает нагреваться до указанных температур и печатает тестовую сетку. Подробнее о калибровке читайте: http://3dtoday.ru/blogs/otumanov/ubl-or-how-to-get-a-perfect-first-layer/

22. <b>Принтер готов к работе</b>.

Подробнее о настройке прошивки для Delta-принтера: http://3dtoday.ru/blogs/xolodny/preparation-and-marlin-firmware-for-delta-printer/



