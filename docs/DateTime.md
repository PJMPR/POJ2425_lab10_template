# 🕒 Obsługa Daty i Czasu w Javie (`java.time`)

Java udostępnia nowoczesny i wygodny sposób pracy z datą i czasem za pomocą pakietu `java.time`. Najważniejsze klasy to:

- `LocalDate` – reprezentuje tylko datę (bez czasu)
- `LocalTime` – reprezentuje tylko czas (bez daty)
- `LocalDateTime` – łączy datę i czas

---

## 📅 `LocalDate` – Data

```java
import java.time.LocalDate;

// Dzisiejsza data
LocalDate dzisiaj = LocalDate.now();

// Konkretna data
LocalDate data = LocalDate.of(2024, 3, 26);

// Parsowanie z tekstu
LocalDate parsed = LocalDate.parse("2024-01-01");

// Pobieranie informacji
int rok = dzisiaj.getYear();
int miesiac = dzisiaj.getMonthValue();
int dzien = dzisiaj.getDayOfMonth();
```

### 🔁 Operacje na datach

```java
LocalDate jutro = dzisiaj.plusDays(1);
LocalDate wczoraj = dzisiaj.minusDays(1);

boolean czyPrzyszlosc = dzisiaj.isBefore(LocalDate.of(2030, 1, 1));
```

---

## ⏰ `LocalTime` – Czas

```java
import java.time.LocalTime;

// Bieżący czas
LocalTime teraz = LocalTime.now();

// Konkretna godzina
LocalTime czas = LocalTime.of(14, 30);

// Parsowanie z tekstu
LocalTime parsedTime = LocalTime.parse("08:15");

// Dodawanie czasu
LocalTime zaGodzine = teraz.plusHours(1);
```

---

## 📆 `LocalDateTime` – Data i czas

```java
import java.time.LocalDateTime;

// Obecna data i czas
LocalDateTime teraz = LocalDateTime.now();

// Konkretna data i czas
LocalDateTime spotkanie = LocalDateTime.of(2025, 4, 10, 9, 0);

// Parsowanie
LocalDateTime parsedDT = LocalDateTime.parse("2024-06-01T12:00");

// Dodawanie czasu
LocalDateTime pozniej = teraz.plusDays(2).plusHours(3);
```

---

## 🕹️ Formatowanie i parsowanie dat

```java
import java.time.format.DateTimeFormatter;

LocalDate dzis = LocalDate.now();
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd.MM.yyyy");

String sformatowana = dzis.format(formatter); // "26.03.2025"

// Parsowanie z tego samego formatu
LocalDate parsed = LocalDate.parse("01.01.2023", formatter);
```

---

## 🧠 Wskazówki

- Nowe API (`java.time`) zastępuje przestarzałe klasy jak `Date` czy `Calendar`.
- Wszystkie klasy są niemutowalne – każda operacja tworzy nową instancję.
- Używaj `DateTimeFormatter` do konwersji między `String` a datą/czasem.

---

Korzystanie z `java.time` jest intuicyjne, bezpieczne i bardzo przydatne w codziennej pracy z datą i czasem w Javie. 🌟
