# Особенности языка программирования Rust

*Версия 1.0* 

Язык программирования Rust, определяемый создателями как "язык, позволяющий каждому создавать надёжное и эффективное программное обеспечение", для достижения своих целей балансирует на грани пересечения безопасности, эффективности выполнения и выразительности. Ниже приведено детальное описание его особенностей и то, как они могут повлиять на проекты, использующие Rust в качестве основного языка программирования.

## 1. Минимальный рантайм

Rust не имеет встроенного сборщика мусора или какой-то иной сколь-либо значительной среды выполнения. Весь рантайм языка состоит из начального загрузчика, сервиса аллокации памяти и обработчика паники с разматыванием стека вызовов, которые могут быть реализованы пользователем вместо реализации по умолчанию из стандартной библиотеки языка.

**Это значит, что:**

- 1.1. Rust можно использовать для системного программирования, в том числе для разработки операционных систем и программ для встраиваемых устройств.
- 1.2. Rust не имеет накладных расходов, связанных со сборщиком мусора, таких как общее замедление работы и GC-паузы.
- 1.3. Rust может использоваться для разработки библиотек для других языков программирования, с вызовами по C FFI.
- 1.4. Rust можно легко компилировать в WASM без необходимости прикомпилировать среду выполнения.
- 1.5. В Rust можно (и приходится) вручную размещать объекты на стеке и в куче.
- 1.6. В программах на Rust память освобождается в предсказуемых местах, также возможно ручное уничтожение объектов с освобождением занятой памяти.
- 1.7. Управление памятью в Rust сложнее, чем в большинстве managed-языках программирования и требует больше ручной работы.


## 2. Мощная система типов

Для императивного языка, ориентированного на производительность, Rust имеет достаточно мощную систему типов, с абстракциями, перенесенными из функциональных языков, но реализованными без дополнительных расходов.

**Это значит, что:**

- 2.1. В Rust строгая статическая типизация.
- 2.2. В Rust абстракции с нулевой стоимостью.
- 2.3. Rust имеет алгебраический тип данных, который в том числе используется для представления значений, которые могут отсутствовать или содержать ошибку.
- 2.4. В Rust имеется и широко используется сопоставление с образцом (паттерн-матчинг).
- 2.5. Rust имеет средства параметрического полиморфизма (генерики).
- 2.6. В Rust отсутствует полиморфизм подтипов.
- 2.7. Для описания интерфейсов и задания ограничений на обобщенные типы, Rust использует типажи (классы типов).
- 2.8. Функция в Rust может возвращать значение экзистенциального типа.
- 2.9. Rust имеет недостижимый тип.
- 2.10. В Rust имеется автовыведение типов переменных в зависимости от контекста использования.
- 2.11. В Rust возможно затенение переменных.
- 2.12. Rust имеет кортежи, срезы и замыкания.
- 2.13. Rust имеет ссылочные типы.
- 2.14. Значения в Rust по-умолчанию иммутабельны.
- 2.15. Любое выражение и любой блок кода в Rust (выделенный фигурными скобками) возвращают значение.
- 2.16. В Rust есть тип для представления указателя на функцию и сырого указателя.
- 2.17. Rust не имеет информации о типах во время выполнения: при компиляции происходит стирание типов.


## 3. Высокая надежность

Мощная система типов Rust вместе с правилами владения и заимствования обеспечивают обнаружение большого количества ошибок на этапе компиляции и, как следствие, высокую безопасность итоговой программы. Однако, в ряде случаев программист вынужден разделять с компилятором контроль бесопасности.

**Это значит, что:**

- 3.1. Rust гарантирует безопасность памяти: обращение к неинициализированной памяти, разыменование нулевого указателя, висячие ссылки, двойное освобождение, незаметный выход за границы массива - в safe Rust невозможны.
- 3.2. Компилятор Rust гарантирует потоковую безопасность программы, ошибки, связанные с гонкой данных, исключаются как класс.
- 3.3. Rust статически отслеживает время жизни объектов и следит за соответствием времени жизни ссылок на этапе компиляции.
- 3.4. В особых случаях контроль за безопасностью кода должен взять на себя программист, когда, например, необходимо разыменовать сырой указатель, вызвать небезопасную функцию или реализовать небезопасный типаж.
- 3.5. Блоки кода, за безопасность которых ответственнен программист, а не компилятор, считаются "небезопасными" и всегда помечаются словом `unsafe`.
- 3.6. Rust использует семантику перемещения по-умолчанию.
- 3.7. В Rust невозможно иметь две изменяемые ссылки на один и тот же участок памяти в одно и то же время.
- 3.8. Правила работы с памятью в Rust требуют при проектирования программ явного определения мест владения ресурсами и их заимствования.


## 4. Широкое повторное использование

Rust поощряет повторное использование кода, компонентный подход к разработке, создание библиотек с открытым исходным кодом и непрерывное обновление.

**Это значит, что:**

- 4.1. Rust имеет гибкую и простую в использовании систему модулей и импортов.
- 4.2. Rust ориентирован на компонентный подход к организации программ.
- 4.3. Библиотеки в Rust распространяются в виде исходных кодов.
- 4.4. В Rust имеются средства метапрограммирования на уровне синтаксиса (DSL и генерации кода) в виде декларативных и процедурных макросов.
- 4.5. Rust ориентирован на частый выпуск нововведений и улучшений в язык с сохранением обратной совместимости.
- 4.6. Процесс разработки языка Rust открыт, любой может принять в нем участие.


## 5. Развитые инструменты

Инструменты разработчика в Rust упрощают разработку и позволяют достичь высокой степени автоматизации рабочего процесса.

**Это значит, что:**

- 5.1. Rust имеет стандартную утилиту управления установкой и настройкой версий компилятора и инструментов разработчика `rustup`.
- 5.2. Rust имеет стандартный расширяемый инструмент сборки и управления зависимостями `cargo`.
- 5.3. Rust имеет встроенную поддержку автоматического тестирования.
- 5.4. Rust имеет стандартную утилиту автоматической генерации документации по коду с комментариями `rustdoc`.
- 5.5. Rust имеет стандартную утилиту автоматического форматирования кода `rustfmt`.
- 5.6. Rust имеет дополнительный синтаксический анализатор `clippy`.
- 5.7. Сообщения об ошибках в компиляторе Rust дружелюбны к пользователю, почти всегда они предлагают способ решения проблемы.
- 5.8. Rust имеет стандартный инструмент автоматического исправления ошибок по предложениям компилятора `rustfix`.


## Ссылки

- [Rust official site](https://www.rust-lang.org/)
- [Rust old site](https://prev.rust-lang.org/en-US/)
- [The Rust runtime](https://doc.rust-lang.org/reference/runtime.html)
- [Runtime services](https://github.com/rust-lang/rust/blob/master/library/std/src/rt.rs)
- [Пишем ОС на Rust. Настройка среды. Бинарник для «голого» железа](https://habr.com/ru/post/527682/)
- [C++ быстрее и безопаснее Rust, Yandex сделала замеры](https://habr.com/ru/post/492410/)
- [Выпуск Rust 1.26](https://habr.com/ru/post/358514/)
- [10 неочевидных преимуществ использования Rust](https://habr.com/ru/post/430294/)
