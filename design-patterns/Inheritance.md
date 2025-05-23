# 📚 Dziedziczenie, nadpisywanie metod i konstruktory w Javie

Ten dokument zawiera krótkie i zrozumiałe wprowadzenie do tematu dziedziczenia w języku Java. Dodatkowo przedstawia zagadnienia takie jak nadpisywanie metod, konstruktory, słówko `super` oraz `abstract.

---

## 🧬 1. Dziedziczenie (`extends`)
Dziedziczenie pozwala klasie potomnej przejąć pola i metody klasy bazowej.

### 🔧 Przykład:
```java
class Vehicle {
    void startEngine() {
        System.out.println("Engine started");
    }
}

class Car extends Vehicle {
    void openTrunk() {
        System.out.println("Trunk opened");
    }
}
```

📌 Klasa `Car` dziedziczy metodę `startEngine()` z klasy `Vehicle` i dodaje własną `openTrunk()`.

---

## 🔁 2. Nadpisywanie metod (`@Override`)
Klasa potomna może zmienić (nadpisać) działanie metody odziedziczonej po klasie bazowej.

### 🔧 Przykład:
```java
class Animal {
    void makeSound() {
        System.out.println("Some sound");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Woof!");
    }
}
```
📌 Gdy wywołasz `makeSound()` na obiekcie `Dog`, pojawi się „Woof!”, mimo że metoda istniała już w klasie `Animal`.

---

## 🧱 3. Konstruktory i `super`
Konstruktor klasy potomnej może (i często powinien) wywołać konstruktor klasy bazowej przy użyciu słowa kluczowego `super`.

### 🔧 Przykład:
```java
class Shape {
    String color;

    Shape(String color) {
        this.color = color;
    }
}

class Circle extends Shape {
    double radius;

    Circle(String color, double radius) {
        super(color); // wywołanie konstruktora Shape
        this.radius = radius;
    }
}
```
📌 `super(color)` musi być pierwszą instrukcją w konstruktorze potomnym.

---

## 🧭 4. Klasa abstrakcyjna (`abstract`)
Abstrakcyjna klasa nie może być instancjonowana. Może zawierać metody abstrakcyjne (bez implementacji), które muszą być zaimplementowane przez klasy potomne.

### 🔧 Przykład:
```java
abstract class Tool {
    abstract void use();
}

class Hammer extends Tool {
    @Override
    void use() {
        System.out.println("Hammering nails");
    }
}
```
📌 Nie możesz napisać `new Tool()`, ale możesz stworzyć `new Hammer()` i użyć metody `use()`.

---

## 🧠 5. `abstract` i `super` w metodach
Czasami chcesz nadpisać metodę, ale jednocześnie zachować jej część z klasy nadrzędnej – wtedy używasz `super`. Możesz też łączyć to z metodami abstrakcyjnymi!

### 🔧 Przykład:
```java
abstract class Printer {
    void printHeader() {
        System.out.println("=== Dokument ===");
    }

    abstract void printContent();

    void printDocument() {
        printHeader();
        printContent();
        System.out.println("=== Koniec ===\n");
    }
}

class InvoicePrinter extends Printer {
    @Override
    void printContent() {
        System.out.println("Faktura nr 12345\nKwota: 250.00 PLN");
    }

    @Override
    void printHeader() {
        super.printHeader();
        System.out.println("Firma XYZ Sp. z o.o.");
    }
}
```

### ✅ Wynik wywołania:
```java
Printer printer = new InvoicePrinter();
printer.printDocument();
```
```plaintext
=== Dokument ===
Firma XYZ Sp. z o.o.
Faktura nr 12345
Kwota: 250.00 PLN
=== Koniec ===
```

---

## 🛠️ Podsumowanie
| Pojęcie        | Opis |
|----------------|------|
| `extends`      | Umożliwia dziedziczenie pól i metod |
| `@Override`    | Informuje, że metoda nadpisuje metodę z klasy bazowej |
| `super`        | Umożliwia dostęp do metod i konstruktorów klasy nadrzędnej |
| `abstract`     | Definiuje klasę/metodę, która nie zawiera implementacji |

---
