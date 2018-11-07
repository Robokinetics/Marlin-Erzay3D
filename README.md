# Marlin-Erzay3D
Прошивка Marlin 1.1.9 для принтеров Erzay3D

![Image alt]: (https://github.com/Robokinetics/Marlin-Erzay3D/blob/master/Logo2a.png)

## Основные особенности:
* Конфигурация для Delta;
* Рускоязычный интерфейс с небольшими исправлениями перевода;
* Поддержка SD-карт;
* Поддержка UBL (Унифицированное выравнивание стола);
* Поддержка команды G26 для печати калибровочной сетки;
* Поддержка комманды G33 для калибровки Delta-принтера;
* "Продвинутая пауза" - парковка печатающей головки во время паузы + возможность смены филамента;
* Функция смены, загрузки и выгрузки филамента;
* Активированный SPEAKER (бипер, пищалка), поддержка команды M300;
* Увеличенный диапазон допустимых температур печати для уменьшения вероятности ложного срабатывания защиты от теплоубегания;
* Оригинальное стартовое окно;
* Отключено опускание печатающей головки по завершении операции Homing для предотвращения повреждения высоких напечатанных моделей;
* Активировано дополнительное меню "Быстрые команды" (Изменённое название "Свои команды"). Содержит в себе 4 пункта:
    1) Домой (G28);
    2) Преднагрев PLA;
    3) Преднагрев ABS;
    4) Автокалибровка стола (G28\nG29 P1\nG29 S\nG29 A\nM500).
* Использоване EEPROM для хранения настроек;
* Увеличено время активности шаговых двигателей до двух часов с момента последнего движения;
* Плата BOARD_MKS_GEN_13, дисплей MKS_MINI_12864;
* Добавлена информация о серийном номере принтера;
* И прочее.
