# Harmonogram zadań - biblioteka do planowania i uruchamiania zadań cyklicznych

## 🎯 Cel projektu

Zaprojektowanie i zaimplementowanie biblioteki, która umożliwia definiowanie, planowanie i wykonywanie zadań (`Job`) w oparciu o zdarzenia czasowe, z zastosowaniem wzorca projektowego **Obserwator (Observer)**.

## 📆 Opis funkcjonalności

Biblioteka umożliwia:

* Definiowanie zadań (interfejs `Job`)
* Planowanie zadań z określonym interwałem i liczbą powtórzeń (interfejs `JobScheduler` i klasa `SimpleJobScheduler`)
* Reagowanie na zdarzenia zmiany czasu (`TimeEvent`)
* Uruchamianie zadań w osobnych wątkach
* Zastosowanie wzorca projektowego Obserwator

## 🪡 Struktura projektu

### 1. Interfejs `Job`

```java
public interface Job {
    void execute();
}
```

Reprezentuje pojedyncze zadanie. Implementacje zawierają logikę do wykonania (np. wydruk, zapis do pliku).

---

### 2. Interfejs `JobScheduler`

```java
public interface JobScheduler {
    void schedule(Job job, int intervalSeconds, int repeatCount);
    void start();
    void stop();
}
```

Umożliwia planowanie zadań z podanym interwałem czasowym i liczbą powtórzeń.

---

### 3. Klasa `SimpleJobScheduler`

* Implementuje `JobScheduler`
* Przechowuje listę zaplanowanych zadań
* Uruchamia zadania w osobnych wątkach
* Obsługuje zdarzenia czasowe generowane przez wewnętrzny zegar

---

### 4. Klasa `TimeEvent`

```java
public class TimeEvent {
    private final LocalDateTime currentTime;

    public TimeEvent(LocalDateTime currentTime) {
        this.currentTime = currentTime;
    }

    public LocalDateTime getCurrentTime() {
        return currentTime;
    }
}
```

Zdarzenie reprezentujące zmianę czasu, wykorzystywane przez harmonogram.

---

### 5. Wzorzec projektowy: Obserwator

* Obserwatorzy nasłuchują zdarzeń typu `TimeEvent` generowanych przez `Clock`
* Każde zadanie może być zarejestrowane jako nasłuchujące określonych momentów czasowych

## 🔄 Przykładowy scenariusz

1. Implementacja klasy `PrintJob implements Job`, która wypisuje tekst
2. Zaplanowanie zadania w `SimpleJobScheduler` na 5 powtórzeń co 2 sekundy
3. `Clock` generuje `TimeEvent` co sekundę
4. Scheduler uruchamia zadanie w osobnym wątku, jeśli to odpowiedni czas
5. Po wykonaniu określonej liczby powtórzeń zadanie nie jest już uruchamiane

## 💡 Dodatkowe pomysły

* Logowanie wykonanych zadań do pliku
* Ustawienie daty startu
* Anulowanie zaplanowanego zadania
* GUI (np. Swing) wizualizujące harmonogram
