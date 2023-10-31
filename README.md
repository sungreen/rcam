# Предистория
* https://blenderartists.org/t/reverse-perspective-rendering/1213342
* http://paulbourke.net/miscellaneous/reverseperspective/
* http://paulbourke.net/miscellaneous/reverseperspective/reverseperspective.pdf

# rcam
Патч для Blender, реализующий эффект обратной перспективы для камеры.
В интерфейсе Blender в настройках камеры в режиме "Perspective" добавлен чек "Reverse perspective", который включает выключает эффект.
Эффект доступен во вьюпорте при просмотре в режиме "Камера".
Визуализация реализована для рендера EEVEE.
Важно! Настройки вида камеры в режиме обратной перспективы существенно зависят от значение ***Clip Start (as Near)*** и ***Clip End (as Far)***.


# rcam3
Добавлен ***Reverse Factor*** - параметр с помощью которого можно контролировать эффект обратной перспективы. Параметр меняется от 0 до 1. При значении 0 эффект не проявляется, то есть камера имеет классический перспективный вид. При значении 1 эффект обратной перспективы проявляется полностью - камера имеет вид обратной перспективы. При значении 0.5 - вид камеры соответствует классическому ортогональному виду.
Этот параметр анимируемый, то есть можно делать анимацию перехода вида из перспективной камеры в камеру с видом обратной перспективы.
* https://www.youtube.com/watch?v=QoBpsq06RAU&ab_channel=nikolaysungreen
* https://www.youtube.com/watch?v=3uXdX7Z720w&ab_channel=nikolaysungreen

Есть ошибки по теням и областью видимости (отсечением), пытаюсь разобраться сам, но хотелось бы получить помощь разработчиков Blender
* https://devtalk.blender.org/t/reverse-perspective-eevee-shadow/13985
* https://devtalk.blender.org/t/reverse-perspective-culling-of-objects/14421

# rcam3-cycles
Реализован эффект обратной персперктивы для рендера cycles. Это дает возможность делать более корректные рендеры теней, преломления и отражения света. Настройки камеры независят от ***Clip Start*** и ***Clip End***, а регулируются величиной эффекта перспективы и обратной перспективы при отрицательных значениях. Добавлены настройки tilt&shift, что существенно обогащает политру настроеек.

# сборки
Распространение сборок неочень хорошая идея с точки зрения безопасности.

rcam3-eevee
* blender 3.4 windows https://disk.yandex.ru/d/CVcwmEnbJILRSw
* blender 3.5 windows https://disk.yandex.ru/d/dWmnPHA_rHkbNw

rcam3-cycles
* blender 3.6 windows https://disk.yandex.ru/d/vJXhUvW170x8Ow
* blender 3.6 linux https://disk.yandex.ru/d/av1psZpl4O73Lw 
* blender 4.1 windows https://disk.yandex.ru/d/RiLNM1LDRzikhA
* blender 4.1 linux https://disk.yandex.ru/d/57mqS_k2-e58-A


