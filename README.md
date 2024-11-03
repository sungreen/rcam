# Концепт универсальной 3D камеры с изменяемой перспективой
## Введение
  В традициях 3D моделирования использовать два основных типа проекции - перспективная и ортогональная. На основе этих типов проекций реализованы представления результатов моделирования во всех без исключения 3D-редакторах и рендерах, при этом такие реализации разделяют эти два типа проекций на отдельные характеристики используемой в 3D сцене камеры. То есть в большинстве случаев для камеры нельзя плавно изменить вид с ортогональной проекции на перспективную. Такой переход происходит только после смены типа камеры.
  В отличие от этого в предлагаемом концепте применяется условный коэффициент Kf, который определяет фактор перспективы таким образом, что при Kf = 0 перспектива отсутствует, что является ортографической проекцией, при Kf > 0 проявляется эффект прямой перспективы, а при Kf < 0 проявляется эффект обратной перспективы. При этом чем больше отличие Kf от нуля тем сильнее проявляется эффект перспективы в одну или другую сторону.
  
![Демонстрация камеры с динамической перспективой](https://github.com/sungreen/rcam/blob/master/Demo/dynamic_perspective.gif)

  Изначально коэффициент Kf имел одинаковое влияние по всем осям. Это позволяет сохранять линейность объектов при прямой и обратной перспективе. Однако если применить различные коэффициенты для осей, то линейность пропадает, перспектива наделяется анизотропией.
  Эффект анизотропной перспективы резулируется параметром Ka. При Ka = 0 анизотропии нет. Перспектива одинаково распространяется по всех осям. При Ka = 1 - перспектива по одной оси полностью отсутствует, а при Ka = 2 - начинает действовать в противоположном направлении.

![Демонстрация камеры с анизотропной перспективой](https://github.com/sungreen/rcam/blob/master/Demo/anisotropy_perspective.gif)

[Видео на рутубе](https://rutube.ru/video/86346a12c6ffc02ba9d3c53ad013cd6d/)
  
Для сборки Blender необходимо ознакомиться с инструкциями с официального сайта [Building Blender](https://wiki.blender.org/wiki/Building_Blender)

Загрузите последнюю версию исходного кода с сайта project.blender.org.

mkdir ~/blender-git

cd ~/blender-git

git clone https://projects.blender.org/blender/blender.git

cd blender

make update

Скачайте файл с патчем rcam4

wget https://raw.githubusercontent.com/sungreen/rcam/master/rcam4_410_20231120.diff

Примените патч к коду Blender

patch -p1 < rcam4_410_20231120.diff

Продолжите сборку Blender

make

## Использование
* rcam3 (устарело)
* rcam4 https://youtu.be/Q2toaIhXuNs

## Готовые сборки Blender с патчем rcam3/rcam4

Распространение сборок неочень хорошая идея с точки зрения безопасности. Тем неменее они есть и их можнос скачать
### rcam3-eevee
* blender 3.4 windows https://disk.yandex.ru/d/CVcwmEnbJILRSw
* blender 3.5 windows https://disk.yandex.ru/d/dWmnPHA_rHkbNw

### rcam3-cycles
* blender 3.6 windows https://disk.yandex.ru/d/vJXhUvW170x8Ow
* blender 3.6 linux https://disk.yandex.ru/d/av1psZpl4O73Lw 
* blender 4.1 windows https://disk.yandex.ru/d/RiLNM1LDRzikhA
* blender 4.1 linux https://disk.yandex.ru/d/57mqS_k2-e58-A

### rcam4-cycles_eevee
* blender 4.1 windows https://disk.yandex.ru/d/0YmJ_aZftWXIzA
* blender 4.1 linux https://disk.yandex.ru/d/QKdIrgmmgeJGgA

### rcam4 blender with anisotropy perspective
* blender 4.4 windows https://disk.yandex.ru/d/r4PRvoGa4friYA
  

## Предистория
* https://blenderartists.org/t/reverse-perspective-rendering/1213342
* http://paulbourke.net/miscellaneous/reverseperspective/
* http://paulbourke.net/miscellaneous/reverseperspective/reverseperspective.pdf

## rcam
Патч для Blender, реализующий эффект обратной перспективы для камеры.
В интерфейсе Blender в настройках камеры в режиме "Perspective" добавлен чек "Reverse perspective", который включает выключает эффект.
Эффект доступен во вьюпорте при просмотре в режиме "Камера".
Визуализация реализована для рендера EEVEE.
Важно! Настройки вида камеры в режиме обратной перспективы существенно зависят от значение ***Clip Start (as Near)*** и ***Clip End (as Far)***.

## rcam3
Добавлен ***Reverse Factor*** - параметр с помощью которого можно контролировать эффект обратной перспективы. Параметр меняется от 0 до 1. При значении 0 эффект не проявляется, то есть камера имеет классический перспективный вид. При значении 1 эффект обратной перспективы проявляется полностью - камера имеет вид обратной перспективы. При значении 0.5 - вид камеры соответствует классическому ортогональному виду.
Этот параметр анимируемый, то есть можно делать анимацию перехода вида из перспективной камеры в камеру с видом обратной перспективы.
* https://www.youtube.com/watch?v=QoBpsq06RAU&ab_channel=nikolaysungreen
* https://www.youtube.com/watch?v=3uXdX7Z720w&ab_channel=nikolaysungreen

Есть ошибки по теням и областью видимости (отсечением), пытаюсь разобраться сам, но хотелось бы получить помощь разработчиков Blender
* https://devtalk.blender.org/t/reverse-perspective-eevee-shadow/13985
* https://devtalk.blender.org/t/reverse-perspective-culling-of-objects/14421

## rcam3-cycles
Реализован эффект обратной персперктивы для рендера cycles. Это дает возможность делать более корректные рендеры теней, преломления и отражения света. Настройки камеры независят от ***Clip Start*** и ***Clip End***, а регулируются величиной эффекта перспективы и обратной перспективы при отрицательных значениях. Добавлены настройки tilt&shift, что существенно обогащает политру настроеек.

## rcam4
Объединены ранее реализованные эффекты обратной перспективы для EEVEE и Cycles в одном патче. Сейчас для Blender реализована возможность динамической перспективы только в окне 3D редактора, для рендера Cycles и частично EEVEE без поддержки OSL Camera Script.
Добавлен эффект анизотропной перспективы.

## OSL Camera
В качестве примера указанный концепт реализован для 3D редактора Blender в виде бинарных сборок с модифицированными настройками камеры и рендеров Cycles и EEVEE, а также в виде отдельных OSL скриптов для связок 3D редактора и внешнего рендера, таких как 3ds max + VRAY или Cinema 4d + OctaneRender, поддерживающих OSL сценарии для настройки камеры https://github.com/sungreen/rcam/tree/master/OSL%20Scripts .

* https://youtu.be/q3kCHOetuak  3ds max + VRAY
* https://youtu.be/lpp2MyjmMDk  C4D + OCTANE
