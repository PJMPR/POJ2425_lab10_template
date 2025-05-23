# 🧠 Typy danych i zarządzanie pamięcią w Javie

W języku Java istnieje kluczowy podział na:
- **typy wartościowe (prymitywne)**
- **typy referencyjne (obiektowe)**

Te dwa typy różnią się nie tylko sposobem działania, ale też miejscem przechowywania w pamięci: **na stosie (stack)** lub **na stercie (heap)**.

---

## 🧩 Typy wartościowe vs referencyjne

### ✅ Typy wartościowe (prymitywne)

Przykłady: `int`, `double`, `boolean`, `char`, `byte`, `long`, `short`, `float`

- Przechowują **bezpośrednią wartość**.
- Dane są przechowywane **na stosie (stack)**.
- Przypisanie kopiuje wartość:

```java
int a = 10;
int b = a; // b = 10
b++;
System.out.println(a); // 10
```

---

### 📦 Typy referencyjne (obiektowe)

Przykłady: `String`, `ArrayList`, własne klasy (`Product`, `Cart`, itp.), tablice (`int[]`, `String[]`)

- Przechowują **referencję (adres)** do obiektu w pamięci.
- Referencja znajduje się **na stosie**, ale obiekt żyje **na stercie (heap)**.
- Przypisanie kopiuje referencję, nie dane:

```java
Product p1 = new Product("Kubek", 20.0);
Product p2 = p1; // p2 wskazuje na ten sam obiekt co p1
p2.setPrice(25.0);
System.out.println(p1.getPrice()); // 25.0
```

---

## 🧠 Stack vs Heap – różnice w pamięci

### 🗂️ Stack (stos)

- Przechowuje zmienne lokalne i referencje do obiektów.
- Dane są usuwane automatycznie po zakończeniu metody.
- Szybki dostęp, mały rozmiar, struktura LIFO (Last In, First Out).

### 🧱 Heap (sterta)

- Przechowuje **obiekty** i tablice.
- Pamięć zarządzana przez **Garbage Collector**.
- Większy rozmiar, wolniejszy dostęp.
- Obiekt istnieje, dopóki istnieje do niego referencja.

---

## 🔍 Przykład łączący wszystko:

```java
public class Main {
    public static void main(String[] args) {
        int a = 5;                        // na stosie
        Product p = new Product("Kubek", 20.0);  // p na stosie, obiekt na stercie
    }
}
```

| Element         | Gdzie trafia?         | Co zawiera?                             |
|------------------|------------------------|-------------------------------------------|
| `a` (int)         | Stack (stos)           | Wartość `5`                                |
| `p` (referencja)  | Stack (stos)           | Adres do obiektu `Product`                |
| Obiekt `Product`  | Heap (sterta)          | Dane: `"Kubek"` i `20.0`                  |

---

## 📌 Porównanie – podsumowanie

| Cecha                    | Typ wartościowy (prymitywny) | Typ referencyjny (obiektowy) |
|--------------------------|------------------------------|-------------------------------|
| Co przechowuje zmienna? | Wartość                      | Adres (referencję)            |
| Przechowywanie w pamięci| Stos (stack)                 | Stos (referencja) + Sterta (obiekt) |
| Przekazywanie do metod  | Kopia wartości               | Kopia referencji              |
| Możliwość `null`        | ❌ Nie                        | ✅ Tak                         |
| Przykłady               | `int`, `double`, `boolean`   | `String`, `Product`, `List`   |

---

👨‍💻 **Autor:** Adam Urbanowicz 
📅 **Data:** 2025-03-21

