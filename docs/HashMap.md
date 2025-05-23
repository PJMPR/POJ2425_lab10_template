
# 🗺️ Java `HashMap`

`HashMap` to część biblioteki kolekcji w Javie i służy do przechowywania par klucz-wartość. Jest to implementacja interfejsu `Map`.

---

## 🔑 Cechy `HashMap`

- Przechowuje dane w postaci **par klucz–wartość**.
- Klucze muszą być **unikalne**.
- Może zawierać **jedną wartość `null` jako klucz** i **dowolną liczbę `null` jako wartości**.
- Nie gwarantuje zachowania kolejności elementów.
- Wewnętrznie używa funkcji **hashującej** do szybkiego dostępu do danych.

---

## 🧱 Deklaracja i inicjalizacja

```java
import java.util.HashMap;

HashMap<KeyType, ValueType> map = new HashMap<>();
```

### Przykład:
```java
HashMap<String, Integer> ageMap = new HashMap<>();
```

---

## 🛠️ Podstawowe operacje

### 🔹 Dodawanie elementów

```java
map.put("Jan", 25);
map.put("Anna", 30);
```

### 🔹 Odczyt wartości

```java
int age = map.get("Jan");
```

### 🔹 Sprawdzenie obecności klucza lub wartości

```java
map.containsKey("Jan");    // true
map.containsValue(30);     // true
```

### 🔹 Usuwanie elementu

```java
map.remove("Anna");
```

### 🔹 Pobieranie rozmiaru

```java
int size = map.size();
```

### 🔹 Iteracja po elementach

```java
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}
```

---

## ✅ Kiedy używać `HashMap`

- Kiedy potrzebujesz **szybkiego dostępu** do danych na podstawie unikalnego klucza.
- Gdy nie jest wymagana **kolejność** elementów.
- Gdy nie operujesz w środowisku wielowątkowym (lub masz kontrolę nad synchronizacją).

---

