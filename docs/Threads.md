# 🧵 Wątki w Javie — Podstawy pracy z klasą `Thread`

## 🔍 Czym są wątki?

Wątki (ang. *threads*) umożliwiają wykonywanie wielu zadań jednocześnie w ramach jednej aplikacji. Dzięki nim można tworzyć aplikacje bardziej responsywne i wydajne, zwłaszcza przy operacjach I/O, sieciowych czy przetwarzaniu w tle.

## 🧱 Klasa `Thread`

W Javie wątek to obiekt klasy `Thread` lub klasy implementującej interfejs `Runnable`. Każdy wątek reprezentuje oddzielny ciąg instrukcji wykonywanych równolegle.

### ✅ Sposób 1: Dziedziczenie po `Thread`

```java
public class MyThread extends Thread {
    public void run() {
        System.out.println("Wątek działa!");
    }
}

// Uruchomienie:
MyThread t = new MyThread();
t.start();
```

### ✅ Sposób 2: Implementacja interfejsu `Runnable`

```java
public class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Wątek działa!");
    }
}

Thread t = new Thread(new MyRunnable());
t.start();
```

## 🕹️ Kluczowe metody klasy `Thread`

| Metoda        | Opis                                              |
| ------------- | ------------------------------------------------- |
| `start()`     | Uruchamia nowy wątek i wykonuje metodę `run()`    |
| `run()`       | Zawiera kod, który ma być wykonany w wątku        |
| `sleep(ms)`   | Usypia wątek na określoną liczbę milisekund       |
| `interrupt()` | Przerywa działanie wątku (jeśli jest obsługiwane) |
| `isAlive()`   | Zwraca `true` jeśli wątek nadal działa            |

## 🧠 Przykład użycia w projekcie

W projekcie cache słownikowego, wątek może odświeżać dane z pliku CSV co 60 sekund:

```java
public class DictionaryCacheRefresher extends Thread {
    public void run() {
        while (true) {
            try {
                // odśwież dane
                DictionaryCache.getInstance().reload();
                Thread.sleep(60000); // 1 minuta
            } catch (InterruptedException e) {
                break; // zakończ wątek jeśli przerwany
            }
        }
    }
}
```

## 🔐 Wątki a bezpieczeństwo danych

W aplikacjach wielowątkowych konieczne jest dbanie o tzw. **synchronizację**, aby uniknąć błędów typu "race condition". W tym celu stosuje się np.:

* słowo kluczowe `synchronized`,
* klasy z pakietu `java.util.concurrent`, takie jak `ReentrantLock`, `ConcurrentHashMap`, `Executors`.

## 🧵 Alternatywy: `Executors`

Zamiast zarządzać ręcznie wątkami, można użyć:

```java
ExecutorService executor = Executors.newSingleThreadExecutor();
executor.submit(() -> {
    // kod wykonywany w tle
});
```

---

Wątki to potężne narzędzie — kluczowe w nowoczesnym programowaniu równoległym. Opanowanie ich pozwala budować bardziej skalowalne i wydajne aplikacje. 🚀
