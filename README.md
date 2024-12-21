# Курсовая работа: Разработка структуры данных для управления складом производственного участка (C++ Builder)

## Описание

Целью данной курсовой работы является разработка программной модели для управления и мониторинга склада производственного участка. Программа предназначена для организации хранения и учета различных типов товаров, упакованных в бочки, коробки и на поддоны.  Реализована объектно-ориентированная модель с использованием классов и наследования.

## Основные концепции

*   **Объектная модель:**
    *   Иерархия классов для представления разных типов упаковки: `StorageItem` (базовый класс), `Bochka`, `Corob`, `Poddon` (производные классы).
    *   Классы для представления склада: `Cell` (ячейка) и `PantBox` (поле).
*   **Абстракция данных:**
    *   Использование инкапсуляции для защиты внутренних данных классов и предоставления интерфейсов для работы с ними.
    *   Наследование для создания более специализированных классов из общего базового класса.
    *   Использование виртуальных методов для полиморфного поведения.

## Структура данных

### Базовый класс `StorageItem`

### Производные классы

#### Класс `Bochka` (Бочка)

#### Класс `Corob` (Коробка)

#### Класс `Poddon` (Поддон)


### Классы склада

#### Класс `Cell` (Ячейка)

#### Класс `PantBox` (Поле)



## Описание файлов проекта

### `Main_f.h`

*   Объявлены классы для работы с товарами и функции формы.

### `Main_f.cpp`

*   **Глобальные переменные:**
    *   `storageArray`: Динамический массив указателей на базовый класс `StorageItem`.
    *   `NBEER`: Счетчик элементов массива `storageArray`.
*   **Функции сохранения и загрузки:**
    *   `SaveActive`: Записывает данные из `storageArray` в файл. Имя файла берется из `Tedit`.
    *   `WriteStorageItemsToFile`: Записывает данные в файл.
    *   `reed_bClick`: Считывает название файла из `OpenDialog`, открывает файл, читает данные и создает объекты, записывая их в `storageArray`.
*   **Функции визуализации:**
    *   `LetsShow`: Записывает данные из `storageArray` в компонент `main_lv_tov` для отображения.
*   **Управляющие функции:**
    *  `ClFindS`, `ClFindUNSHIFT`, `VisualFormActive`, `SaveActive`, `Closing`, `FindActive`, `FindExit`, `SortType`, `MainPanResize`, `reed_bClick`, `Sortyrovka`, `NewItem`, `Redacted`, `Fresh`, `PopDel`. (Функции для управления интерфейсом, установки флагов и вызова других функций).
*   **Чат:**
    *   `AddChat`, `ChatLoad`, `ReChat`: Загрузка, обновление и сохранение чата.
*    **Массив:**
     *    `ArrayClear`: Очистка массива.
*   **Сравнение и перемещение элементов:**
    *  `moveItemToStart`: Передвигает элемент в начало.
    *   `compareByProductName`: Сравнение элементов по названию продукта.
    *   `compareByZena`: Сравнение элементов по цене.
*   **Сортировка:**
    *   `shellSortByZena`: Сортировка методом Шелла по цене.
    *  `shellSortByProductName`: Сортировка методом Шелла по имени продукта.
*   **Поиск:**
    *  `binarySearch`: Бинарный поиск (применяется для отсортированного массива).
    *   `linearSearch`: Линейный поиск.
  **Оптимизация сбора заказов:**
     *   **Алгоритм:**
            1.  **Сбор данных:**  Функция `GetUniqueZacazValues`  находит уникальные заказы.  Для каждого заказа вычисляется время сборки с помощью  `findPtime`. Функция  `FindZacaz`  находит товары по нужному заказу.
            2.  **Сортировка:** Функция  `sortOrders` сортирует заказы по дедлайну. Дедлайны вводятся пользователем.
            3.  **Планирование:** Функция `sborZ` планирует последовательность сборки заказов, начиная с наиболее срочных.
        *   `findPtime(StorageItem**, int, int*)`: Находит время сбора всех партий в массиве.
        *   `FindZacaz(StorageItem**, int, int*, AnsiString, int&)`: Находит товары по определенному заказу.
        *   `GetUniqueZacazValues(StorageItem*[], int, AnsiString[], int&)`: Находит уникальные заказы.
        *   `sortOrders(AnsiString*, DateM*, int)`: Сортирует заказы по дедлайну.
### `save_f.h`

*   Объявлены функции формы для редактирования и сохранения объектов.

### `save_f.cpp`

*  **Визуализация:**
    * `TupePaint`: Рисование типа объекта на холсте.
    * `Reapint`: Обработчик на выбор типа объекта, разблокирует поля ввода и перерисовывает холст.
*   **Управление формой:**
    *   `Close_Re`, `Close_ReF`, `CleaningR`: Обработчики на закрытие формы и сброс полей.
*  **Сохранение:**
     * `SaveBTN`: Сохранение изменений.
*   **Вспомогательные функции:**
    *  `copyStorageItemsArray`: Копирование массива.
    * `ObjSaving`: Функция с параметрами по умолчанию для изменения/сохранения данных в массиве.
*   **Фильтрация:**
    * `areBothNumbersWritten`, `Filters_Ok`: Использование регулярных выражений для фильтрации ввода данных.

### `visual_f.h`
* Объявление классов для визуализации и функции формы.

### `visual_f.cpp`
* **Визуализация:**
    * `DrawLegend`: Функция рисования легенды на холсте.
    * `DrawField`: Функция рисования поля на холсте.
*   **Маршрутизация:**
    * `calculateDistance`: Расчет расстояния между объектами.
    *  `findNearestNeighbor`: Нахождение ближайшего соседа.
    *  `processItems`: Обработка объектов
    *  `Invent`: Построение оптимального маршрута между объектами одного класса и вывод последовательности.
*   **Управление полем:**
    * `fillField`: Заполнение поля.
    * `isUnique`: Проверка на уникальность.
    *  `Startin`: Функция для управления погрузчиком.
   *  `Button[x]Click` (x э [1;4]): Функции для управления погрузчиком (разные кнопки).
## Технологии и инструменты

*   **Язык программирования:** C++
*   **Среда разработки:** C++ Builder
*   **Система контроля версий:** Git

## Запуск проекта

1.  Клонируйте репозиторий с GitHub.
2.  Откройте проект в C++ Builder.
3.  Скомпилируйте и запустите проект.

## Документация



## Автор

*   Карпов Михаил
*   karpovm2005@gmail.com
