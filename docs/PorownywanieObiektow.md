
# 📘 Porównywanie obiektów i wartości w Java

W Javie istnieją **dwa sposoby porównywania obiektów**:

---

## ✅ Porównywanie wartości (`equals()`)

Używamy metody `.equals()` do **sprawdzenia, czy dwa obiekty mają taką samą zawartość (czyli wartości pól)**.

### 🔧 Przykład:
```java
Person p1 = new Person(1, "Ala", LocalDate.of(2000, 1, 1));
Person p2 = new Person(1, "Ala", LocalDate.of(2000, 1, 1));

p1.equals(p2); // true, jeśli metoda equals została poprawnie nadpisana
```

> 🧠 Domyślnie metoda `equals()` porównuje **referencje**, a nie wartości.  
Dlatego trzeba ją **nadpisać** w klasie.

---

## 🧪 Porównywanie referencji (`==`)

Operator `==` porównuje, czy **dwa obiekty wskazują na to samo miejsce w pamięci**.

### 🔧 Przykład:
```java
Person p1 = new Person(1, "Ala", LocalDate.of(2000, 1, 1));
Person p2 = p1;

p1 == p2; // true (bo to ta sama referencja)

p1.equals(p2); // też true
```

Ale:
```java
Person p1 = new Person(1, "Ala", LocalDate.of(2000, 1, 1));
Person p2 = new Person(1, "Ala", LocalDate.of(2000, 1, 1));

p1 == p2;      // false
p1.equals(p2); // true (jeśli equals jest nadpisane)
```

---

## 🧮 `hashCode()` – co to jest i po co?

Metoda `hashCode()` **zwraca liczbę całkowitą**, która reprezentuje obiekt. Jest używana m.in. w kolekcjach takich jak `HashMap`, `HashSet`.

> Jeśli dwa obiekty są równe (`equals()`), muszą mieć też ten sam `hashCode()`.

### 🔧 Przykład użycia:
```java
Map<Person, Address> map = new HashMap<>();
map.put(p1, address);
```

Jeśli `hashCode()` nie jest spójny z `equals()`, może się okazać, że `map.containsKey(p2)` zwróci `false`, mimo że `p1.equals(p2)`!

---

## ✨ `toString()` – przyjazne wypisywanie obiektów

Metoda `toString()` pozwala **zdefiniować, jak ma wyglądać tekstowa reprezentacja obiektu**.

### 🔧 Przykład:
```java
System.out.println(p1);
// np: (1, Ala, 2000-01-01)
```

Zamiast domyślnego:
```
com.example.Person@1a2b3c
```

### 💡 Wskazówka:
Warto użyć `StringBuilder`, jeśli składamy kilka linii tekstu, np. z adresami.

---

## 🧷 Podsumowanie

| Sytuacja                      | Co użyć?     |
|------------------------------|--------------|
| porównanie zawartości obiektów | `equals()`   |
| porównanie referencji         | `==`          |
| użycie w HashMap/HashSet     | `equals()` + `hashCode()` |
| czytelne wypisywanie         | `toString()`  |
