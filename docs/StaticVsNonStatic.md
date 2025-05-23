# 📄 Pamięć dla pól statycznych i niestatycznych w Javie

W języku **Java** pola statyczne i niestatyczne (instancyjne) są przechowywane w różnych obszarach pamięci i mają różne zasady inicjalizacji oraz użytkowania.

---

## 🔢 1. Pola statyczne (`static`)

- ✅ **Pamięć przydzielana jest raz** dla całej klasy.
- 📊 Przechowywane są w obszarze **Metaspace** (od JDK 8; w JDK 7 i wcześniejszych był to **PermGen**).
- ⏱️ Rezerwacja pamięci podczas **ładowania klasy** przez ClassLoader.
- 🤝 Współdzielone przez wszystkie instancje danej klasy.

### 📝 Przykład:
```java
public class MyClass {
    static int counter = 0; // jedno miejsce w pamięci, dzielone
}
```

---

## 📁 2. Pola niestatyczne (instancyjne)

- 🌟 **Pamięć przydzielana jest osobno dla każdej instancji** klasy.
- 🛠️ Przechowywane są w **heapie** jako część obiektu.
- ✨ Rezerwacja pamięci w momencie **tworzenia obiektu** (`new`).
- 👤 Każdy obiekt ma **własną kopię** tych pól.

### 📝 Przykład:
```java
public class MyClass {
    int id = 0; // każda instancja ma własną kopię
}
```

---

## 📈 Podsumowanie

| 🔍 Cechy              | 🔹 Pola statyczne              | 🔹 Pola niestatyczne           |
|--------------------------|----------------------------|----------------------------|
| Powiązanie               | Z klasą                    | Z obiektem                 |
| Liczba kopii             | Jedna (wspólna)            | Każda instancja ma swoją |
| Czas inicjalizacji       | Przy ładowaniu klasy       | Przy tworzeniu obiektu    |
| Obszar pamięci (JVM)     | Metaspace (PermGen do JDK 7) | Heap                       |

---

👤 **Autor**: Adam Urbanowicz  
📅 **Data**: 2025-03-21

