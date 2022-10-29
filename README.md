# Java Virtual Machine
При запуске JVM, работают три загрузчика классов(classloaders):
* Bootstrap class loader (Загрузчик класса Bootstrap)
* Extensions class loader (Загрузчик класса расширений)
* System class loader (Системный загрузчик классов)
  ### Stacks
  Одновременно с потоком в JVM создаётся стек. Стек в JVM хранит frames. Стек — это место, где создаются ссылки и локальные переменные, содержащие примитивы, при этом локальные переменные ссылочного типа будут указывать на память, выделяемую в куче
  Куча(heap) — это место, где в основном создаются объекты. Куча создается при запуске виртуальной машины. Хранилище для объектов восстанавливается автоматической системой управления данными (известной как сборщик мусора).
  Frame используется для хранения данных и частичных результатов, а также для выполнения динамического связывания, возврата значений для методов и отправки исключений. Новый frame создается каждый раз, когда вызывается метод.
  Сущность, которая чистит мусор, — одна из важнейших служб. Она влияет на правильную работу приложения. Обычно для сборки мусора происходит приостановка программы — Stop The World. Пауза — это полная остановка потоков программы для безопасной сборки мусора.
  Недостижимые объекты удаляются, достижимые объекты группируются по времени жизни (поколения). Чем дольше объект живёт, тем реже проверяют, нужно ли его удалить.
  Далее описание программы класса JvmComprehension посторочно и попунктно:
* 1 Во frame main создается переменная  i, значение = 1
* 2 Переменная о создается в stack фрейма main и хранит в себе ссылку на объект, new Object сохраняется в heap.
* 3 Integer является ссылочной переменной ii, помещается в stack main и хранит в себе ссылку на значение объекта Integer, значение объекта сохраняется в heap.
* 4 В stack создается frame printAll
* 7 В stack формируется frame println, в котором создается ссылка на объект String "finished". Объект String сохраняется в heap.
* 5 В stack во frame printAll для хранения создается  переменная uselessVar, которая хранит в себе ссылку на объект Integer. Объект со значением 700 сохраняется в heap.
* 6 В stack создаются frame println и toString. В frame println передаются переменные i со значением 1, ii, o, последние из которых хранят ссылки на объекты Object o, Integer ii.
