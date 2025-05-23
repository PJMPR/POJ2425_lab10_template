
# 🧠 Praca z `HashMap` w Javie – przykład

Ten przykład pokazuje, jak można wykorzystać klasę `HashMap` w języku **Java** do przechowywania i wyszukiwania obiektów według unikalnego klucza.

---

## 📦 Przykład: Produkty w sklepie

W aplikacji definiujemy klasę `Product`, która reprezentuje produkt z następującymi polami:

- `productKey` – unikalny identyfikator (np. kod produktu),
- `name` – nazwa produktu,
- `price` – cena produktu.

Następnie tworzymy kilka produktów i dodajemy je do `HashMap`, gdzie:

- **kluczem** jest `productKey`,
- **wartością** jest obiekt klasy `Product`.

```java
HashMap<String, Product> productsByCode = new HashMap<>();
productsByCode.put(chleb.productKey, chleb);
productsByCode.put(szynka.productKey, szynka);
productsByCode.put(skarpety.productKey, skarpety);
```

---

## 🔍 Wyszukiwanie elementu

Aby znaleźć produkt po jego kodzie:

```java
Product productWithCode002 = productsByCode.get("002");
System.out.println("Product z kodem 002 to " + productWithCode002.name);
```

---

## 🔁 Iteracja po elementach

Możemy przejść przez wszystkie produkty w mapie:

```java
for (String key : productsByCode.keySet()) {
    Product p = productsByCode.get(key);
    System.out.println("Product z kodem " + key + " to " + p.name);
}
```

---

## 📌 Podsumowanie – co pokazuje ten przykład:

- Tworzenie i używanie `HashMap` z własnymi klasami.
- Wstawianie (`put`) i pobieranie (`get`) obiektów z mapy.
- Iterowanie po kluczach (`keySet()`).
- Prosty przykład zastosowania `HashMap` jako słownika do szybkiego wyszukiwania danych.

---

## 🧪 Pełny kod źródłowy

```java
package com.pjatk.bank;

import java.util.HashMap;

public class FunWithHashMaps {

    public static void main(String[] ars){

        Product chleb = new Product("001", "Chleb", 2);
        Product szynka  = new Product("002", "Szynka", 5);
        Product skarpety = new Product("003", "Skarpety", 10);

        HashMap<String,Product> productsByCode = new HashMap<>();

        productsByCode.put(chleb.productKey, chleb);
        productsByCode.put(szynka.productKey, szynka);
        productsByCode.put(skarpety.productKey, skarpety);

        Product productWithCode002 = productsByCode.get("002");

        System.out.println("Product z kodem 002 to " + productWithCode002.name);

        System.out.println("\n========== Wszystkie produkty ============\n");
        for (String key : productsByCode.keySet()){
            Product p = productsByCode.get(key);
            System.out.println("Product z kodem " + key + " to " + p.name);
        }

    }

}

class Product {
    String productKey;
    String name;
    double price;

    public Product(String productKey, String name, double price) {
        this.name = name;
        this.price = price;
        this.productKey = productKey;
    }
}
```
