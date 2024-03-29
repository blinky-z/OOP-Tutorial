# Помощник в освоении ООП

Данная мини-книжка создана помочь в освоении Объектно-ориентированного программирования (ООП).

**Содержание:**
- [Словарь терминов](#словарь-терминов)
- [Парадигмы программирования](#парадигмы-программирования)
    - [Императивные парадигмы](#императивные-парадигмы)
        - [Процедурное программирование](#процедурное-программирование)
        - [Объектно-ориентированное программирование](#объектно-ориентированное-программирование)
    - [Декларативные парадигмы](#декларативные-парадигмы)
        - [Функциональное программирование](#функциональное-программирование)
- [Что такое ООП? Зачем оно нужно? Как оно используется?](#что-такое-ооп-зачем-оно-нужно-как-оно-используется)
- [Как проектировать программы с ООП?](#как-проектировать-программы-с-ооп)
    - [Паттерны проектирования](#паттерны-проектирования)
- [Базовые принципы ООП](#базовые-принципы-ооп)
    - [Наследование](#наследование)
    - [Полиморфизм](#полиморфизм)
    - [Инкапсуляция](#инкапсуляция)
- [Что такое класс?](#что-такое-класс)
    - [В чем различия между классом и структурой?](#в-чем-различия-между-классом-и-структурой)
- [Что такое объект](#что-такое-объект)
    - [Отличия между классом и объектом](#отличия-между-классом-и-объектом)
- [Модификаторы доступа](#модификаторы-доступа)
    - [Применение модификаторов к членам класса](#применение-модификаторов-к-членам-класса)
        - [Public](#public)
        - [Private](#private)
        - [Protected](#protected)
    - [Применение модификаторов к унаследованным классам](#применение-модификаторов-к-унаследованным-классам)
- [Виртуальная функция](#виртуальная-функция)
    - [Чистая виртуальная функция](#чистая-виртуальная-функция)
- [Таблица виртуальных функций](#таблица-виртуальных-функций)
- [Friend functions](#friend-functions)
- [Статические поля класса](#статические-поля-класса)
- [Статические методы класса](#статические-методы-класса)
- [Scope resolution operator](#scope-resolution-operator)
- [Что такое конструктор?](#что-такое-конструктор)
    - [Default constructor](#default-constructor)
    - [Parameterized constructor](#parameterized-constructor)
    - [Вызов конструктора](#вызов-конструктора)
- [Initializer list](#initializer-list)
    - [Применение Initializer list](#применение-initializer-list)
- [Что такое деструктор?](#что-такое-деструктор)
    - [Виртуальный деструктор](#виртуальный-деструктор)
- [Абстрактный класс](#абстрактный-класс)
- [Геттеры \& Сеттеры](#геттеры--сеттеры)
    - [Связь с инкапсуляцией](#связь-с-инкапсуляцией)
- [Разделение класса на описание и имплементацию](#разделение-класса-на-описание-и-имплементацию)
    - [Достоинства данного метода](#достоинства-данного-метода)
- [RAII](#raii)
    - [Действия в случае исключения](#действия-в-случае-исключения)
- [Smart pointers](#smart-pointers)
    - [Отличия между unique\_ptr и shared\_ptr](#отличия-между-unique_ptr-и-shared_ptr)

---

## Словарь терминов

- **Полиморфизм** - это способность языка программирования вызывать необходимую имплементацию в зависимости от типа данных. В данном справочнике будет рассмотрен *Runtime* полиморфизм.
- **Метод** - методом называется какая-либо функция класса
- **Поле класса** - полем называется какая-либо переменная класса

---

## Парадигмы программирования

Прежде чем приступать к изучению ООП и ответу на вопрос зачем оно нужно, сначала надо изучить самые основные парадигмы и понять разницу между ними.

**Парадигма** - это стиль написания программ, подходы к написанию кода.

Парадигмы делятся на 2 типа: **[императивная](https://ru.wikipedia.org/wiki/%D0%98%D0%BC%D0%BF%D0%B5%D1%80%D0%B0%D1%82%D0%B8%D0%B2%D0%BD%D0%BE%D0%B5_%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5)** и **[декларативная](https://ru.wikipedia.org/wiki/%D0%94%D0%B5%D0%BA%D0%BB%D0%B0%D1%80%D0%B0%D1%82%D0%B8%D0%B2%D0%BD%D0%BE%D0%B5_%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5)**. Императивная парадигма программированию задает последовательность команд, *КАК* надо что-то сделать, а декларативное - *ЧТО* надо сделать.

### Императивные парадигмы

#### Процедурное программирование

Вся программа - набор переменных, их состояний, они постоянно меняются пока программа идет к конечному результату. Программа содержит набор подпрограмм (процедур), с помощью которых вычисляются нужные значения, меняются какие-то переменные. В языках C и C++ их роль выполняют функции.

#### Объектно-ориентированное программирование

Именно эту парадигму мы рассматриваем в данной книжке.

---

### Декларативные парадигмы

#### Функциональное программирование

Абсолютно противоположная императивному парадигма. Тут нет переменных, нет состояний.
Новые переменные создаются путем передачи нужных аргументов в функции, где уже создаются новые значения, а из тех же функций снова в другие.
Поэтому основной принцип работы программы - рекурсия.
Это защищает данные от изменения, так как на каждом шаге программы мы работает всегда с новыми данными, и повлиять на
прошлые никак не можем. То есть программа работает только с локальными данными, передаваемыми в функции.

---

## Что такое ООП? Зачем оно нужно? Как оно используется?

ООП построена на основе процедурного программирования.

Однако оно решает её самую главную проблему - в процедурном значения переменных могут меняться извне,
потому что они доступны глобально. Вызывая какие-нибудь функции, мы рискуем повлиять на работу совершенно других
переменных/функций. ООП же, в свою очередь, завязан на работе только с отдельными объектами.
Это защищает данные от внезапного изменения, так как вызывая какой-нибудь метод, пользователь работает лишь с конкретным объектом.

---

## Как проектировать программы с ООП?

1. Как и приступая к написанию кода большинства программ, для начала следует разобраться с архитектурой программы, продумать все алгоритмы, а не сразу начинать писать код, требуется полностью понять как должна работать будущая программа.
2. Стоит помнить о такой вещи в ООП, как принцип единственной ответственности. Каждый класс должен быть ответственен только за одну вещь и отвечать за конкретную цель.

    При изменении кода в одном месте, это может затронуть совершенно другие функции, изменение которых пользователь может совершенно не ожидать, так как они преследуют совершенно другие цели, но из-за того, что все имплементировано в одном классе, мы рискуем получить ошибку. При чем, принцип единственной ответственности предполагает, что вся важнейшая имплементация будет инкапсулирована.
3. Программа должна быть разбита на отдельные модули, каждый модуль отвечает за отдельные вещи.

    При чем, они должны быть связаны минимально, то есть изменение кода в одном классе должно быть относительно безболезненным, чтобы потом не пришлось переделывать всю программу.
4. Программа должна быть читабельна, а структура программы понятна, не должно быть анархии в коде.

    Один из способов сделать это - при написании программы отделять интерфейс программы от их имплементации, инкапсулируя имплементацию нижнего уровня, а также ненужную информацию, которая потребуется лишь в ходе работы самой программы, то есть вещи которые происходят внутри нее, но не в ходе ее использования, предоставляя лишь нужный интерфейс к доступу функций.

---

### Паттерны проектирования

**Паттерн проектирования** - это общепринятый метод решения какой-либо проблемы в программировании. Это НЕ готовая программа, а лишь описание ее решения. Паттерны упрощают проектирование программ за счет того, что использовать готовое решение гораздо проще и надежнее, ведь паттерны это уже закрепленные и проверенные практики в мире программирования. Более того, это также сводит к минимуму возможность возникновения ошибок.

Примеры паттернов:
1. *Итератор* - это паттерн, который позволяет последовательно обходить все элементы объекта, не зная его внутренней имплементации.

    Пример:

    ```c++
        vector <int> data;
        vector <int>::iterator it;
        int value = 0;

        for (it = data.begin(); it != data.end(); it++) {
            value++;
            *it = value;
        }
    ```

2. *[Абстрактная фабрика](https://refactoring.guru/ru/design-patterns/abstract-factory)*
3. И многие другие. Есть отличный сайт по паттернам проектирования - [Refactoring.Guru](https://refactoring.guru/ru/design-patterns/catalog)

---

## Базовые принципы ООП

### Наследование

**Наследование** - это возможность создать новый дочерний класс на основе родительского класса, но с расширением функциональности. При чем, все методы родительского класса будут доступны и в дочернем.

Пример:

```c++
#include <iostream>
using namespace std;
class Base {
public:
    string s;
    void initialize_string(const string& data) {
        s = data;
    }
};
class Derived : public Base { // Дочерний класс
public:
    void print_string() {
        cout << s;
    }
};
int main() {
    Derived object;
    object.initialize_string("Derived class was created");
    object.print_string(); // Derived class was created
    return 0;
}
```

### Полиморфизм

**Полиморфизм** - это возможность использовать объекты c одинаковым интерфейсом одного класса, но на основе типа объекта.

Это значит то, что основной интерфейс у них не отличается ничем друг от друга, но некоторые методы должны работать в зависимости от типа объекта. Тогда создается несколько методов, имеющих одинаковое объявление, но различную имплементацию, внутри одного класса и его потомков. Более подробно данная особенность будет рассмотрена позднее в главе "Виртуальные функции".

Пример:

```c++
#include <iostream>
using namespace std;

class Base {
public:
    virtual void print() {
        cout << "Base class print function was called" << endl;
    }
};

class Derived : public Base {
public:
    void print() override { // Пример полиморфизма: функция была объявлена ранее в родительском классе,
        // однако при вызове функции print() из объекта типа Derived будет вызвана данная функция, а не
        // родительского класса
        cout << "Derived class print function was called" << endl;
    }
};

int main () {
    Base* parent = new Base;
    Derived child;

    parent->print(); // Base class print function was called

    delete parent;

    parent = &child; // Смена типа объекта на тип дочернего класса

    parent->print(); // Derived class print function was called
    return 0;
}
```

### Инкапсуляция

**Инкапсуляция** - это сокрытие деталей имплементации в классе. Доступ к необходимым данным предоставлен через специальные паблик методы.
Следование данному принципу защищает данные от внезапного изменения извне и от непредвиденных ошибок.

Пример:

```c++
#include <iostream>
using namespace std;

class Rectangle {
protected:
    double width, height;
public:
    void set_values(int a, int b) { // Скрытые переменные должны инициализироваться паблик методами,
        // таким образом защищая их от изменения извне
        width = a;
        height = b;
    }
};

int main () {
    Rectangle figure = Rectangle();
    figure.set_values(4, 10);
    return 0;
}
```

---

## Что такое класс?

**Класс** - это тип данных, задаваемый пользователем, следовательно, функциональность и имплементация класса полностью зависят от самого пользователя.

Создание класса:

```c++
#include <iostream>
using namespace std;

class Foo {
public:
    Foo() {
        cout << "Class was created";
    };
};

int main() {
    return 0;
}
```

---

### В чем различия между классом и структурой?

Класс от структуры отличает то, что в классе все поля по умолчанию имеют модификатор private, а в структуре - public.

---

## Что такое объект

**Объект** - это конкретный экземпляр класса, функциональность которого полностью ограничена самим классом. Класс - всего лишь описание, на него не
выделяется памяти. Для того, чтобы стало возможным записывать данные и вызывать методы, требуется создать объект. Все состояния переменных класса
будут принадлежать конкретному объекту (кроме статических полей, которые будут рассмотрены позднее).

Создание объекта:

```c++
#include <iostream>
using namespace std;

class Foo {
public:
    Foo() {
        cout << "Class was created";
    }
};

int main() {
    Foo object; // Объект создан
    return 0;
}
```

---

### Отличия между классом и объектом

Класс лишь определяет доступные поведения, методы, возможные состояния экземпляров класса (объектов), а сами объекты -
это конкретные экземпляры класса, в них мы можем вызывать методы, создавать переменные, при чем все они могут иметь
различные состояния, но будут контролироваться классом. Все доступные методы и поведение описано в классе, через объекты
происходит взаимодействие с классом и хранение данных.

---

## Модификаторы доступа

Модификаторы доступа позволяют настраивать область видимости в программе конкретных методов/переменных, описанных в классе.

### Применение модификаторов к членам класса

#### Public

**Public** - данный модификатор позволяет получать доступ к переменным/методам из любого места программы. Никакие данные не скрыты,
область видимости - глобальная.

Пример:

```c++
#include <iostream>
using namespace std;

class Foo {
public:
    string s;
};

int main() {
    Foo object;
    object.s = "Class was created"; // обращение к переменной класса без использования паблик-методов
    return 0;
}
```

#### Private

**Private** - данный модификатор ограничивает область видимости переменных/методов, делая их доступными только в самом классе.
Доступ к ним можно будет получить только через паблик методы класса.

Пример:

```c++
#include <iostream>
using namespace std;

class Foo {
private:
    string s;
public:
    void initialize_string(const string& data) {
        s = data;
    }

    void print_string() {
        cout << s;
    }
};

int main() {
    Foo object;
    object.initialize_string("private modifier is set"); // Для того, чтобы получить доступ к переменной,
    // объявленной как private, требуется обращаться к ней через паблик функции класса
    object.print_string(); // private modifier is set
    return 0;
}
```

#### Protected

**Protected** - данный модификатор отличается от private только тем, что данные, объявленные как protected, могут быть получены из дочерних классов, созданных на основе родительского (также это известно как наследование, разобранное и описанное выше).

Пример:

```c++
#include <iostream>
using namespace std;

class Base {
//private: // Ошибка: получить доступ к переменной в дочернем классе будет невозможно
protected:
    string s;
};

class Derived : Base {
public:
    void initialize_string(const string& data) {
        s = data;
    }

    void print_string() {
        cout << s;
    }
};

int main() {
    Derived object;
    object.initialize_string("protected modifier is set");
    object.print_string(); // protected modifier is set
    return 0;
}
```

---

### Применение модификаторов к унаследованным классам

Все описанные модификаторы доступа применимы также и к модификаторам доступа наследственных классов:

1. **Public** - при применении к унаследованному классу означает то, что доступ к Base классу смогут получить **все классы, которые имеют доступ к дочернему-классу Derived**

    ```c++
    Class Derived : public Base {};
    ```

2. **Protected** - при применении к унаследованному классу означает то, что доступ к Base классу смогут получить все те классы, которые **были унаследованы от дочернего класса Derived**

    ```c++
    Class Derived : protected Base {};
    ```

3. **Private** - при применении к унаследованному классу означает то, что доступ к Base классу сможет получить **только дочерний класс**

    ```c++
    Class Derived : private Base {};
    ```

---

## Виртуальная функция

**Виртуальная функция** (virtual function) - это метод в родительском классе, который можно переопределить в его дочерних классах. Это позволяет пользователю вызывать необходимые методы в зависимости от типа объекта (см. [#Базовые принципы ООП: Полиморфизм](#полиморфизм)).

Пример:

```c++
#include <iostream>
using namespace std;

class Base {
public:
    void print() {
        cout << "In parent class";
    }
};

class Derived : public Base {
public:
    void print() {
        cout << "In child class";
    }
};

int main () {
    Base* baseptr = new Base; // Объект типа родительского класса

    baseptr->print(); // In parent class
    cout << endl;

    delete baseptr;
    baseptr = new Derived; // Объект типа дочернего класса

    baseptr->print(); // In parent class
    delete baseptr;
    return 0;
}
```

Как видно из примера, функция `print()`, вызванная из объекта типа `Derived`, в любом случае вызывает функцию родительского класса.
Это происходит потому, что функция `print()` вызывается в зависимости от типа *указателя*, а не объекта. Виртуальные функции же решают эту проблему и позволяют вызывать методы на основе типа *объекта*, что известно как **Runtime polymorphism**.

Объявляем функцию `print()` как *виртуальную*:

```c++
#include <iostream>
using namespace std;

class Base {
public:
    virtual void print() {
        cout << "In parent class";
    }
};

class Derived : public Base {
public:
    void print() override {
        cout << "In child class";
    }
};

int main () {
    Base* baseptr = new Base; // Объект типа родительского класса

    baseptr->print(); // In parent class
    cout << endl;

    delete baseptr;
    baseptr = new Derived; // Объект типа дочернего класса

    baseptr->print(); // In child class
    delete baseptr;
    return 0;
}
```

---

### Чистая виртуальная функция

**Чистая виртуальная функция** (pure virtual function) - это виртуальная функция, не имеющая имплементации в родительском классе. Необходимость в ней возникает, когда пользователь не знает, какая имплементация должна быть у виртуальной функции в родительском классе, так как ее имплементация зависит от типа объекта. Чистую виртуальную функцию требуется инициализировать нулевым значением.

Пример:

```c++
#include <iostream>
#include <cmath>
using namespace std;

class Shape {
protected:
    int width = 0, height = 0;
public:
    void set_values(int a, int b) {
        width = a;
        height = b;
    }

    // Тип объекта не известен (квадрат или прямоугольник),
    // следовательно имплементация метода в родительском классе невозможна
    virtual double get_diagonal() = 0;

};

class Square : public Shape {
public:
    double get_diagonal() override {
        return sqrt(2 * pow(width, 2));
    }
};

class Rectangle : public Shape {
public:
    double get_diagonal() override {
        return sqrt(pow(width, 2) + pow(height, 2));
    }
};

int main () {
    Shape* shape;
    Square square;
    Rectangle rectangle;

    shape = &square;
    shape->set_values(5, 5);
    cout << shape->get_diagonal() << endl; // 7.07107

    shape = &rectangle;
    shape->set_values(4, 3);
    cout << shape->get_diagonal(); // 5
    return 0;
}
```

---

## Таблица виртуальных функций

Как было уже сказано ранее, виртуальные функции поддерживают **Runtime** полиморфизм. Он имплементируется автоматически компилятором с помощью
виртуальной таблицы функций. Говоря кратко, виртуальная таблица класса - это список указателей на методы, которые должны будут вызываться,
в зависимости от типа объекта. Виртуальная таблица создается для каждого класса, который имеет виртуальный метод, или для унаследованных от него.
Если виртуальная функция была переопределена в классе, то виртуальная таблица для данного класса будет иметь указатель на метод в данном классе,
иначе указатель будет иметь адрес метода в классе, в котором виртуальный метод был впервые объявлен (в основном, родительский класс).

---

## Friend functions

**Friend function** - это функция, объявленная вне области класса и его потомков, однако имеющая доступ к скрытым данным (private и protected) в нем.

Пример:

 ```c++
#include <iostream>
using namespace std;

class Foo {
private:
    int a;
public:
    friend void print_value(Foo Foo); // Объявление дружественной функции (keyword "friend")

    int set_values(int value) {
        a = value;
    }
};

void print_value(Foo Foo) { // Дружественная функция, имеющая доступ к скрытым данным в классе Foo
    cout << Foo.a;
}

int main () {
    Foo foo = Foo();
    foo.set_values(5);
    print_value(foo); // 5
    return 0;
}
 ```

---

## Статические поля класса

**Статическое поле** - это член класса, который имеют общее состояние во всех созданных объектах. Следовательно, при изменении значения члена
класса в одном объекте, оно изменится и во всех созданных объектах того же типа класса.

Пример:

```c++
#include <iostream>
using namespace std;

class Foo {
public:
    static int s;
};

int Foo::s = 0;

int main() {
    Foo first;
    Foo second;

    first.s = 5;

    cout << first.s; // 5
    cout << endl;
    cout << second.s; // 5
    // Переменная s во втором объекте имеет то же состояние, что и первый объект
    return 0;
}
```

Вопрос: Для чего требуется выносить инициализацию переменной за класс?

```c++
int Foo::s = 0;
```

Ответ: Так как статическая переменная не является частью конкретных объектов, а принадлежит самому классу, то и инициализируется она при начале работы
программы. Также, если класс со статическим полем определен в хедере, то при включении хедера во множественных местах, переменная будет объявляться
более одного раза, что запрещено. Поэтому ее определение требуется вынести за область видимости класса.

Важно отметить, что пользователь может получить к ним доступ, даже не создавая объект. Такой метод доступа
к данным наиболее предпочтителен, чем доступ через объекты, так как корректнее считать, что статическое поле относится к самому *классу*, а не к
конкретному объекту. Пример:

```c++
#include <iostream>
using namespace std;

class Foo {
public:
    static int s;
};

int Foo::s = 0;

int main() {
    Foo first;
    Foo second;

    first.s = 5;

    cout << first.s; // 5
    cout << endl;
    cout << second.s; // 5
    // Переменная s во втором объекте имеет то же состояние, что и первый объект
    return 0;
}
```

Также следует отметить, что при инициализации доступ к статической переменной может быть получен независимо от ее модификаторов доступа.

И наконец логичным заключением из вышенаписанного является то, что что статическая переменная хранит свое состояние от начала работы программы и до конца, ведь она принадлежит классу, а не объекту.

---

## Статические методы класса

**Статический метод** - статический метод так же, как и статическая переменная, может быть вызван без создания объекта. Также он нужен для того,
чтобы получить доступ к скрытым статическим полям в классе, так как получить доступ к скрытой переменной напрямую невозможно (но ее все также можно
инициализировать). Для того, чтобы это стало возможным, требуется создать статический класс.

Пример:

```c++
#include <iostream>
using namespace std;

class Foo {
private:
    static int s;
public:
    static int get_value() {
        return s;
    }
};

int Foo::s = 10;

int main() {
    cout << Foo::get_value(); // 10
    return 0;
}
```

Следует отметить, что статический метод может получить доступ только к таким же *static* полям класса, но не *non-static* переменным.

Также определение метода может быть вынесено за область видимости класса. Пример:

```c++
#include <iostream>
using namespace std;

class Foo {
private:
    static int s;
public:
    static int get_value();
};

int Foo::get_value() {
    return s;
}

int Foo::s = 10;

int main() {
    cout << Foo::get_value(); // 10
    return 0;
}
```

---

## Scope resolution operator

[Scope resolution operator](https://en.wikipedia.org/wiki/Scope_resolution_operator) `::` позволяет получать доступ к области видимости какого-либо класса, и, соответственно, к переменным/методам в нем.

---

## Что такое конструктор?

**Конструктор** - это специальный метод класса, который инициализирует объекты. Конструктор вызывается автоматически при создании объекта.
Если пользователь не написал свой конструктор, компилятор автоматически генерирует пустой конструктор.

Существует 2 типа конструкторов:

### Default constructor

**Стандартный конструктор** - это конструктор, который не имеет никаких параметров.

Пример:

```c++
#include <iostream>
using namespace std;

class Foo {
public:
    int a, b;

    Foo() { // Конструктор
        a = 5;
        b = 7;
    }
};

int main () {
    Foo construct;

    cout << construct.a; // 5
    cout << endl;
    cout << construct.b; // 7
    return 0;
}
```

**Стандартный конструктор будет автоматически генерироваться компилятором, если не были объявлены никакие другие специализированные конструкторы.**
В противном случае необходимо имплементировать стандартный конструктор самому пользователю. Без стандартного конструктора невозможно создание
дочерних классов или объектов данного класса в дочерних классах.

### Parameterized constructor

**Parameterized constructor**, в отличие от стандартного конструктора, имеет параметры в своем объявлении и позволяет инициализировать поля класса
переданными параметрами.

Пример:

```c++
#include <iostream>
using namespace std;

class Foo {
public:
    int a, b;

    Foo(int a1, int a2) { // Конструктора
        a = a1;
        b = a2;
    }
};

int main () {
    Foo construct(10, 15);

    cout << construct.a; // 10
    cout << endl;
    cout << construct.b; // 15
    return 0;
}
```

### Вызов конструктора

Вызвать конструктор можно двумя способами:

1. Для *стандартного* конструктора:

    ```c++
    Construct explicit_call = Construct(); // Явный вызов
    Construct implicit_call; // Неявный вызов
    ```

2. Для *parameterized* конструктора:

    ```c++
    Construct explicit_call = Construct(parameters); // Явный вызов
    Construct implicit_call(parameters); // Неявный вызов
    ```

Существует значимое отличие явного вызова от неявного при использовании стандартного конструктора. Если конструктор не имплементирован, и
происходит явный вызов, то все значения будут инициализированы нулями. Однако, при использовании неявного вызова компилятор будет использовать
стандартный конструктор, который ***не инициализирует*** значения нулями, присваивая случайные значения.

---

## Initializer list

**Initializer list** требуется для того, чтобы инициализировать переменные класса.

Однако существует огромная разница между инициализацией членов класса с помощью initializer list и присваиванием значений в теле конструктора. Initializer list принимает аргументы и *сразу же инициализирует* необходимые данные в отличие от присваивания в теле конструктора, где сначала компилятором *создается копия* переданных данных и только после этого происходит присваивание. Следовательно, использование первого метода положительно влияет на скорость выполнения программ.

Пример использования:

```c++
#include <iostream>
using namespace std;

class Foo {
private:
    int a, b;
public:
    Foo(int i, int j) : a(i), b(j) {}; // Initializer list

    int get_a() {
        return a;
    }

    int get_b() {
        return b;
    }
};

int main() {
    Foo foo = Foo(5, 8);

    cout << foo.get_a(); // 5
    cout << endl;
    cout << foo.get_b(); // 8
    return 0;
}
```

### Применение Initializer list

Существует несколько случаев, где применим только *initializer list*:

- Для инициализации константных переменных в классе:

    ```c++
    #include <iostream>
    using namespace std;

    class Foo {
    private:
        const int s;
    public:
        // Valid
        Foo(int i = 0) : s(i) {};

        /* Invalid
        Foo(int i = 0) {
            s = i;
        };
        */

        int get_value() {
            return s;
        };
    };

    int main() {
        Foo foo = Foo(19);

        cout << foo.get_value(); // 19
        return 0;
    }
    ```

- Для инициализации Reference Members (переменных, которым присвоен адрес какой-либо другой переменной)

    ```c++
    #include <iostream>
    using namespace std;

    class Foo {
    private:
        int& s; // Переменная содержит адрес переменной x и изменяется при изменении последней
    public:
        // Valid
        Foo(int& i) : s(i) {};

        /* Invalid: переменной s невозможно присвоить адрес переменной i таким образом
        Foo (int& i) {
            s = i;
        }
        */

        int get_value() {
            return s;
        };
    };

    int main() {
        int x = 10;

        Foo foo = Foo(x);

        cout << foo.get_value(); // 10
        cout << endl;

        x = 25;

        cout << foo.get_value(); // 25
        return 0;
    }
    ```

- Для инициализации объектов, которые не имеют стандартного конструктора.

    Пример:

    ```c++
    #include <iostream>
    using namespace std;

    class Foo {
    protected:
        int i;
    public:
        Foo(int a) {
            i = a;
            cout << "Foo's constructor called" << endl;
        };
    };

    class Bar {
    private:
        Foo foo;
    public:
        // Valid: инициализация объекта foo с использованием parameterized конструктора
        Bar(int a) : foo(a) {
            cout << "Bar's constructor called";
        };

        /* Invalid: невозможно инициализировать объект таким образом
        Bar(int a) {
            a_object = Foo(a);
        }
        */
    };

    int main() {
        Bar object(10);
        return 0;
    }
    ```

- Для инициализации членов класса, которые имеют такое же имя, как и переданный параметр

    Пример:

    ```c++
    #include <iostream>
    using namespace std;

    class Foo {
    private:
        int i;
    public:
        // Valid
        Foo(int i) : i(i) {
            cout << "Data member i was initialized to: " << Foo::i;
        };

        /* Invalid: переменная i класса Foo инициализируется не должным образом, выводя случайные значения из мусора
        Foo(int i) {
            i = i;
            cout << "Data member i was initialized to: " << Foo::i; // Data member i was initialized to: 432910816
        }
        */
    };

    int main() {
        Foo foo(10); // Data member i was initialized to: 10
        return 0;
    }
    ```

---

## Что такое деструктор?

**Деструктор** - это специальный метод класса, который высвобождает память, которая использовалась во время жизненного цикла объекта, и уничтожает
объект. Он вызывается автоматически при завершении жизненного цикла объекта. В деструкторе можно описать пользовательские действия, и перед тем,
как объект полностью уничтожится, требуемые действия будут произведены. Например: закрыть открытый файл, высвободить динамически выделенную
память и т.д.

Важно отметить, что деструктор вызывается только если объект был полностью инициализирован без ошибок и без исключений.

Пример простого деструктора:

```c++
#include <iostream>
using namespace std;

class Destruct {
public:
    int a = 5, b = 10;

    ~Destruct() {
        cout << "Object was deleted";
    }
};

int main () {
    Destruct example;
    return 0; // Object was deleted
}
```

### Виртуальный деструктор

Виртуальный деструктор требуется для полного корректного уничтожения объекта, где содержится хотя бы 1 виртуальный метод. Уничтожение объекта по указателю типа *родительского класса* является неопределенным поведением, так как происходит вызов деструктора по типу *указателя*, а не типу объекта (это описано подробнее в главе о [Виртуальных функциях](#виртуальная-функция)). Для того, чтобы полностью удалить объект, требуется добавить виртуальные деструкторы во все унаследованные классы.

Пример:

```c++
#include <iostream>
using namespace std;

class Base {
public:
    Base() {
        cout << "Constructing Base" << endl;
    }

    virtual ~Base() {
        cout << "Destructing Base" << endl;
    }
};

class Derived : public Base {
public:
    Derived() {
        cout << "Constructing Derived" << endl;
    }

    ~Derived() override {
        cout << "Destructing Derived" << endl;
    }
};

int main() {
    Base *d = new Derived();
    // Constructing Base
    // Constructing Derived

    delete d;
    // Destructing Derived
    // Destructing Base
    return 0;
}
```

---

## Абстрактный класс

**Абстрактный класс** - это класс, который имеет чистую виртуальную функцию (см. [#Чистая виртуальная функция](#чистая-виртуальная-функция)).
Абстрактный класс не может быть инициализирован. Он используется для дальнейшего создания объектов конкретного типа, которые будут иметь
функциональность родительского класса, но различную имплементацию виртуальных и чистых виртуальных методов.
- Если виртуальная функция не была переопределена в дочернем классе, дочерний класс также будет являться абстрактным классом.

Пример:

```c++
#include <iostream>
using namespace std;

class Foo {
public:
    virtual void pure_virtual_function() = 0;
};

int main() {
    // Foo foo; // Ошибка создания объекта типа абстрактного класса
    return 0;
}
```

---

## Геттеры & Сеттеры

**Getter** - метод класса, возвращающий данные пользователю

**Setter** - метод класса, инициализирующий данные переданными аргументами.

Пример:

```c++
#include <iostream>
using namespace std;

class Base {
private:
    int s;
public:
    int set_value(int a) { // Setter
        s = a;
    }

    int get_value() { // Getter
        return s;
    }
};

int main() {
    Base base;

    base.set_value(5);

    cout << "The variable s was set to: " << base.get_value(); // The variable s was set to: 5
    return 0;
}
```

### Связь с инкапсуляцией

Геттеры и сеттеры тесно связаны с инкапсуляцией (см. [#Базовые принципы ООП: Инкапсуляция](#инкапсуляция): так как принцип инкапсуляции предполагает скрытие деталей имплементации от пользователя, то для того, чтобы управлять скрытыми данными, требуются специальные паблик методы -
геттеры и сеттеры.

---

## Разделение класса на описание и имплементацию

Класс также можно разделить на описание и имплементацию и подключить его в виде библиотеки.
Пример:

Содержимое файла **Foo.h**. Описание класса.

```c++
#ifndef OOP_LEARN_FOO_H
#define OOP_LEARN_FOO_H

class Foo {
private:
    int s;
public:
    Foo();

    int set_value(int a);

    int get_value();
};

#endif
```

Содержимое файла **Foo.cpp**. Имплементация класса.

```c++
#include <iostream>
#include "Foo.h"
using namespace std;

Foo:: Foo() {
    s = 0;
    cout << "Constructor was called in the Foo header file" << endl;
}

int Foo::set_value(int a) {
    s = a;
}

int Foo::get_value() {
    return s;
}
```

Программа с классом Base, имплементированным в виде библиотеки:

```c++
#include <iostream>
#include "Foo.h"
using namespace std;

int main() {
    Foo foo; // Constructor was called in the Foo header file

    foo.set_value(5);

    cout << "The variable was set to: " << foo.get_value(); // The variable was set to: 5
    return 0;
}
```

### Достоинства данного метода

- Класс можно использовать в различных файлах, просто включив библиотеку в программу, что поможет избежать дублирования кода.
- От пользователя скрыта имплементация методов, так как в хедере содержится лишь описание класса. Это также помогает другим пользователям класса
лучше понять написанный код, не отвлекаясь не детали имплементации.
- Легче проделывать какие-либо изменения в коде, так как для этого потребуется только найти нужные файлы, где имплементирован класс, а не искать среди огромного количества строк кода.

---

## RAII

**RAII (Resource Acquisition Is Initialization)** - идиома ООП, заключающаяся в том, что:
- выделение ресурсов для требуемых действий в классе должно происходить во время инициализации объекта
- освобождение, соответственно, во время его уничтожения, таким образом привязывая используемые ресурсы к времени жизни объекта

**RAII** - это требование безопасности выделения ресурсов и их последующего освобождения, а также безопасности работы программы в случае исключения. Каждый программист должен писать программы, следуя RAII.

*Ресурс* - это не только выделенная память, а также открытие файлов, установка соединения с сервером и другое. Но все это должно освобождаться в конце жизненного цикла, таким образом исключая утечки и ошибки в работе программе.

### Действия в случае исключения

Если при инициализации объекта произошла ошибка или исключение, то может произойти утечка памяти, так как некоторые выделенные в динамической памяти члены класса не будут высвобождены.

Пример программы, в которой происходит утечка памяти из-за исключения:

```c++
#include <iostream>
using namespace std;

class Foo {
private:
    int* arr;
public:
    Foo() {
        arr = new int[3]{1, 2, 3}; // Память, выделенная под массив, не освободится
        throw runtime_error("watch out memory leaks!");
    }
};

int main() {
    try {
        Foo foo;
    }
    catch (exception e) {

    }
}
```

Запустим [Valgrind](https://valgrind.org/):

```text
==4734== LEAK SUMMARY:
==4734==    definitely lost: 12 bytes in 1 blocks
==4734==    indirectly lost: 0 bytes in 0 blocks
==4734==      possibly lost: 0 bytes in 0 blocks
```

Для того, чтобы исправить утечку памяти, следует использовать **[smart pointer](https://en.wikipedia.org/wiki/Smart_pointer)**, который *автоматически* вызывает соответствующий типу указателя оператор высвобождения памяти, когда указатель выходит из области видимости и соответственно при завершении программы ошибкой.

Пример программы, использующей *smart pointer*:

```c++
#include <iostream>
#include <memory>

using namespace std;

class Foo {
private:
    unique_ptr <int[]> arr;
public:
    Foo() {
        arr = unique_ptr<int[]>(new int[3]{1, 2, 3}); // Smart pointer
        throw runtime_error("no memory leaks");
    }
};

int main() {
    try {
        Foo foo;
    }
    catch (exception) {

    }
}
```

Запустим [Valgrind](https://valgrind.org/):

```text
==6432== LEAK SUMMARY:
==6432==    definitely lost: 0 bytes in 0 blocks
==6432==    indirectly lost: 0 bytes in 0 blocks
==6432==      possibly lost: 0 bytes in 0 blocks
```

Утечка исчезла, ошибка исправлена.

Следует отметить, что в случае исключения при инициализации будут вызваны деструкторы других объектов, которые были уже инициализированы в конструкторе класса A, но не деструктор самого класса A.

Пример:

```c++
#include <iostream>
using namespace std;

class Foo {
public:
    ~Foo() {
        cout << "Foo's destructor" << endl;
    }
};

class Bar {
private:
    Foo foo;
public:
    Bar() {
        foo = Foo();

        throw runtime_error("error");
    }

    ~Bar() {
        cout << "Bar's destructor" << endl;
    }
};

int main() {
    Bar bar;
    return 0;
    // Foo's destructor
}
```

---

## Smart pointers

**Smart pointer** - это указатель, который автоматически удаляет объект в конце его жизненного цикла (вызывая требуемый оператор `delete`/`delete[]` или же деструктор класса).

Пример автоматического высвобождения памяти:

```c++
#include <iostream>
#include <memory>
using namespace std;

int main() {
    unique_ptr <int[]> ptr(new int[100]);

    return 0;
}
```

Запустим [Valgrind](https://valgrind.org/):

```text
==12154== LEAK SUMMARY:
==12154==    definitely lost: 0 bytes in 0 blocks
==12154==    indirectly lost: 0 bytes in 0 blocks
==12154==      possibly lost: 0 bytes in 0 blocks
```

Существует 2 наиболее используемых умных указателя: **unique_ptr** и **shared_ptr**.

### Отличия между unique_ptr и shared_ptr

Используя **unique_ptr**, пользователь может создать *только один* указатель на какой-либо объект.

Пример:

```c++
#include <iostream>
#include <memory>
using namespace std;

int main() {
    unique_ptr <int[]> ptr(new int[10]);
    unique_ptr <int[]> newptr = ptr; // Ошибка

    return 0;
}
```

И напротив, **shared_ptr** же позволяет создать *множество указателей* на объект.

Пример:

```c++
#include <iostream>
#include <memory>
using namespace std;

int main() {
    shared_ptr <int[]> ptr(new int[10]);
    shared_ptr <int[]> newptr = ptr; // Корректно

    return 0;
}
```
