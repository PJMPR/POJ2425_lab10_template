# 📚 Java ArrayList – podstawy i przykłady

`ArrayList` to dynamiczna tablica z biblioteki standardowej Javy, należąca do pakietu `java.util`. Umożliwia przechowywanie elementów w kolejności ich dodania, pozwala na duplikaty i dynamicznie zwiększa swój rozmiar.

---

## 🔧 Tworzenie listy

```java
import java.util.ArrayList;

ArrayList<String> fruits = new ArrayList<>();
ArrayList<Integer> numbers = new ArrayList<>();
```

---

## ➕ Dodawanie elementów

```java
fruits.add("Apple");
fruits.add("Banana");
fruits.add("Orange");

numbers.add(1);
numbers.add(2);
numbers.add(3);
```

Dodanie na konkretną pozycję:

```java
fruits.add(1, "Kiwi"); // Wstawia na indeks 1, przesuwa resztę
```

---

## 🔍 Przeglądanie elementów

### Pętla `for-each`:
```java
for (String fruit : fruits) {
    System.out.println(fruit);
}
```

### Pętla `for` z indeksem:
```java
for (int i = 0; i < fruits.size(); i++) {
    System.out.println(fruits.get(i));
}
```

---

## 🔎 Szukanie i dostęp

```java
String value = fruits.get(2);       // Pobiera element na indeksie 2
int index = fruits.indexOf("Banana"); // Zwraca indeks (lub -1 jeśli nie znaleziono)
boolean exists = fruits.contains("Kiwi"); // true/false
```

---

## ❌ Usuwanie elementów

```java
fruits.remove("Orange");     // Usuwa pierwsze wystąpienie "Orange"
fruits.remove(1);             // Usuwa element o indeksie 1
fruits.clear();               // Usuwa wszystkie elementy
```

---

## 🔗 Łączenie kolekcji

```java
ArrayList<String> moreFruits = new ArrayList<>();
moreFruits.add("Mango");
moreFruits.add("Pineapple");

fruits.addAll(moreFruits); // Dodaje wszystkie elementy z drugiej listy
```

---

## 🏣 Przykład z obiektami: Produkty

Załóżmy, że mamy klasę `Product`:

```java
public class Product {
    private String name;
    private double price;

    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public String getName() { return name; }
    public double getPrice() { return price; }

    @Override
    public String toString() {
        return name + " - " + price + " zł";
    }
}
```

### Tworzenie listy produktów

```java
ArrayList<Product> products = new ArrayList<>();
products.add(new Product("Kubek", 20.0));
products.add(new Product("Notes", 15.5));
products.add(new Product("Długopis", 5.0));
```

### Iterowanie po liście

```java
for (Product p : products) {
    System.out.println(p);
}
```

### Wyszukiwanie produktu

```java
for (Product p : products) {
    if (p.getName().equals("Notes")) {
        System.out.println("Znaleziono produkt: " + p);
    }
}
```

### Znalezienie indeksu

```java
int index = -1;
for (int i = 0; i < products.size(); i++) {
    if (products.get(i).getName().equals("Kubek")) {
        index = i;
        break;
    }
}
System.out.println("Indeks kubka: " + index);
```

---

## 🔗 Łączenie kolekcji produktów

```java
ArrayList<Product> extra = new ArrayList<>();
extra.add(new Product("Teczka", 35.0));

products.addAll(extra);
```

---

## 📀 Najważniejsze metody `ArrayList`

| Metoda                | Opis                                      |
|-----------------------|-------------------------------------------|
| `add()`               | Dodaje element                            |
| `get(index)`          | Zwraca element o danym indeksie           |
| `set(index, value)`   | Nadpisuje wartość                         |
| `remove()`            | Usuwa po indeksie lub po wartości         |
| `contains()`          | Sprawdza, czy element istnieje            |
| `indexOf()`           | Zwraca pierwszy indeks wystąpienia        |
| `size()`              | Zwraca ilość elementów                    |
| `isEmpty()`           | Sprawdza, czy lista jest pusta            |
| `clear()`             | Czyści listę                              |
| `addAll(Collection)`  | Łączy z inną kolekcją                     |

---

## 💬 Uwagi

- `ArrayList` działa bardzo wydajnie przy dodawaniu i odczycie na końcu.
- Nie nadaje się do częstych wstawek/usuwania w środku – do tego lepsza będzie `LinkedList`.

---

👨‍💻 **Autor:** Adam Urbanowicz
📅 **Data:** 2025-03-21

