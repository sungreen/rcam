# Предистория
https://blenderartists.org/t/reverse-perspective-rendering/1213342
http://paulbourke.net/miscellaneous/reverseperspective/
http://paulbourke.net/miscellaneous/reverseperspective/reverseperspective.pdf

# rcam
Патч для Blender, реализующий эффект обратной перспективы для камеры.
В интерфейсе Blender в настройках камеры в режиме "Perspective" добавлен чек "Reverse perspective", который включает выключает эффект.
Эффект доступен во вьюпорте при просмотре в режиме "Камера".
Визуализация реализована для рендера EEVEE.
Важно! Настройки вида камеры в режиме обратной перспективы существенно зависят от значение Clip Start(Near) и Clip End(Far).


# rcam3
Добавлен Reverse Factor - параметр с помощью которого можно контролировать эффект обратной перспективы. Параметр меняется от 0 до 1. При значении 0 эффект не проявляется, то есть камера имеет классический перспективный вид. При значении 1 эффект обратной перспективы проявляется полностью - камера имеет вид обратной перспективы. При значении 0.5 - вид камеры соответствует классическому ортогональному виду.
Этот параметр анимируемый, то есть можно делать анимацию перехода вида из перспективной камеры в камеру с видом обратной перспективы.
https://www.youtube.com/watch?v=f2j9RLgXEKA
https://www.youtube.com/watch?v=0G-ECJmtQm0
https://www.youtube.com/watch?v=wvCle7iyxd4

Есть ошибки по теням и областью видимости (отсечением), пытаюсь разобраться сам, но хотелось бы получить помощь разработчиков Blender
https://devtalk.blender.org/t/reverse-perspective-eevee-shadow/13985
https://devtalk.blender.org/t/reverse-perspective-culling-of-objects/14421
