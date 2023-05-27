# Общие критерии

## Что должно быть в хорошем README?
При использовании собственного ПО для полетного контроллера и наличия решения CV задачи, необходимо два различных репозитория.
Хороший ридми подразумевает краткое описание используемых вами технологий и идей. Желательно написать на каком этапе разработки данное ПО сейчас, список дальнейших задач (TODO).

### ПО для полетного контроллера
В случае ПО "с нуля" желательно описать для какого железа вы писали ПО, сослаться на используемы библиотеки для получения данных с датчиков, кратко описать алгоритм СУ. В самом идеалальном случае должна быть инструкция, по которой любой желающий человек мог бы воспроизвести ваши разработки, т.е. используемая среда разработки, дополнительные библиотеки, зависимость от версий, схема платы, как прошить и т.д. Но за отсутсвие таковой баллы сниматься не будут.

В случе использования готового ПО за основу (например, вы сделали форк Ardupilot или PX4 и внесли туда свои изменения), оригинальное ридми нужно удалить, вместо него оставить ссылку на исходный репозиторий и описать какие изменения вы внесли в проект и зачем. Оригинальная история изменений должна сохраниться (не надо удалять .git), чтобы можно было посомотреть, какие изменения в проект внесли именно вы.

### Задача CV
Краткое описание алгоритма, датасета, способа его создания, железа, на котором запускается или планируется запускать алгоритм. Пример полученных результатов.


# Примеры


## OurAutopilot
В репозитории представлен прототип автопилота для ____.

### Железо
*Если используется плата собственной разработки*

Проект запускается на следующем железе:
микроконтроллер: STM32H743IIT6,
барометр: MS5611
...
Подробная схема представлена в папке (файле) asdasd

*Или модель используемого готового полетного контроллера.*

### ПО
пример хорошего описания: https://docs.px4.io/main/en/concept/architecture.html, можно не так подробно.

## OurArdupilotModification
Оригинальный репозиторий: https://github.com/ArduPilot/ardupilot.

В проект добавлен драйвер для датчика BestBaroSensor444 в libraries/AP_Baro/. 

Написан hwdef для собственной платы в AP_HAL_ChibiOS/hwdef/BestFC777

### Краткое описание платы
*ваше описание*

Подробная схема находится тут - (файл, ссылка).

## OurCV
**В репозитории представлен алгоритм детекции и определения местоположения изображений армянских букв на бумаге.**

*фото с примером буквы*

Алгоритм состоит из 3 часей:

1) Определение областей, потенциально содержащие буквы внутри себя. Делается переводом изображения в HSV и выбора белых областей на изображении по порогу H.
2) Подача выбранных областей в сверточную нейронную сеть для классификации буквы. Архитектура нейросети представлена на изображении ниже
*изображение*
3) Определение координат букв. Координаты определяются путем линейного пересчета пикселей смещения области от центра в метры. GPS координаты центра берутся из полетного контроллера по протоколу Mavlink (вычислитель и полетный контроллер подключены по UART)

### Железо
В качестве вычислителя используется *ваш вычислитель*. Приведенный алгоритм на нем работает в 228 fps. Камера - Sony IMX123. 

### Пример результата работы
*ваше фото/видео с примером работы алгоритма*

### Todo
- [ ] Попробовать заменить первые два этапа работы алгоритма на алгоритм детекции YOLOV3. 
- [ ] Сделать работу алгоритма независимой от высоты. Т.е. коэффициенты пересчета в координаты зависят от текущей высоты, получаемой от полетного контроллера.

### In Progress
- [ ] Перекалибровать коэффициенты пересчета в метры из пикселей на высоте 100м.  

### Done 
- [x] Добавить поворотные аугментации при обучении.

## Пример плохого описания CV
Для решения задачи использовалась сверточная нейронная сеть.
