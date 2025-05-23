## 🧩 Interfejsy w języku Java

### ❓ Co to jest interfejs?

Interfejs w języku Java to kontrakt, który określa zestaw metod, jakie muszą być zaimplementowane przez klasę go implementującą. Interfejsy pozwalają na:

* ✅ definiowanie wspólnego zachowania dla różnych klas,
* 🔁 osiągnięcie **polimorfizmu**,
* 🧪 programowanie zgodne z zasadą "programuj do interfejsu, nie do implementacji".

---

### 🏗️ Jak zdefiniować interfejs?

```java
public interface Drivable {
    void start();
    void stop();
}
```

---

### 🚗 Implementacja interfejsu w klasie

```java
public class Car implements Drivable {
    public void start() {
        System.out.println("Samochód rusza");
    }
    public void stop() {
        System.out.println("Samochód się zatrzymuje");
    }
}
```

---

### ⚙️ Wykorzystanie interfejsu

```java
Drivable vehicle = new Car();
vehicle.start();
vehicle.stop();
```

Dzięki interfejsowi możemy pisać kod, który nie zależy od konkretnej klasy (`Car`), a tylko od zachowania (`Drivable`).

---

## 🔁 Polimorfizm

### ❓ Co to jest polimorfizm?

Polimorfizm to zdolność obiektów do przyjmowania wielu form. W kontekście Javy oznacza to, że obiekt może być traktowany jako instancja interfejsu, który implementuje, lub klasy bazowej, po której dziedziczy.

---

### 🧪 Przykład:

```java
public interface Shape {
    void draw();
}

public class Circle implements Shape {
    public void draw() {
        System.out.println("Rysuję koło");
    }
}

public class Square implements Shape {
    public void draw() {
        System.out.println("Rysuję kwadrat");
    }
}

public class Painter {
    public void paint(Shape shape) {
        shape.draw();
    }
}
```

---

### 🖼️ Użycie:

```java
Painter painter = new Painter();
Shape shape1 = new Circle();
Shape shape2 = new Square();
painter.paint(shape1);
painter.paint(shape2);
```

---

### 🎯 Co to daje?

* ✅ możliwość pisania elastycznego i rozszerzalnego kodu,
* 🔌 rozdzielenie implementacji od użycia,
* 🧪 ułatwienie testowania i rozwoju oprogramowania.

---

## 📏 Dobre praktyki

* 🚫 Unikaj tworzenia interfejsów zawierających zbyt wiele metod (stosuj zasadę segregacji interfejsów).
* 🧠 Nazywaj interfejsy rzeczownikami opisującymi rolę (np. `Printable`, `Sortable`).
* 📦 Interfejsy to nie klasy abstrakcyjne – nie mogą mieć pól (poza `public static final`) i domyślnych konstruktorów.

---

