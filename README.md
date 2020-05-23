### PixelPlanetBot based on Selenium
 
Usage: pixelplanet.py [-h] [--step N] [--headless]
                      [--direction {horizontal,vertical}]
                      [--method {default,chessboard,random}]
                      x y image

После появления капчи, решите её и введите Enter в терминале, чтобы продолжить рисование.
 
Так как бот не знает о цвете конкретной координаты, он будет пытаться на каждой поставить соответствующий изображению пиксель. Каждый раз, когда он ставит (или думает, что ставит) пиксель, он ждет 0.5 секунды (можно поставить любое значение от 0.2 до 0.5 секунды, но глобально от этого ничего не изменится). 
 
Для защиты артов использовать не очень удобно, удобнее рисовать картинки, так как бот последовательно проходит через всё изображение. 
 
Те пиксели, в которых альфа канал < 20%, будут пропущены. Перед использованием любой картинки **ВАЖНО** сконвертировать её предварительно через игровой конвертор, иначе при встрече несуществующего в палитре цвета, бот просто поставит белый пиксель.

`--step` - смещение по изображению, чтобы не ждать пока бот пройдет уже нарисованное, отображается в выводе терминала во время рисования. То есть можно запомнить значение step и продолжить рисовать арт с этого места позже.

`--headless` - запуск chrome в headless режиме (не будет отображаться ui хрома, что может повысить производительность, но для просмотра арта придется открывать отдельный браузер). Когда бот остановится из-за капчи, введите её в отдельном браузере. Если бот, запущенный с headless опцией, завершится аварийно, то процессы браузера могут продолжить висеть в оперативной памяти, так что их нужно будет удалить вручную.

`--direction` - способ рисования. Сверху вниз (horizontal) или слева направо (vertical). Любой рисунок следует рисовать единственным выбранным вначале способом.

`--method` - тоже способ рисования, но немного о другом. Последовательно (default), в шахматном порядке (chessboard), рандомная выборка (random). Несмотря на то, что в последнем варианте изображение рисуется в хаотичном порядке, тем не менее можно использовать step, так как для каждого изображения генерируется единственный хаотичный порядок (константный seed). 