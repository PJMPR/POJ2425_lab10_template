# ⏰ `ScheduledExecutorService` w Javie — planowanie zadań w tle

## 🔍 Czym jest `ScheduledExecutorService`?

`ScheduledExecutorService` to interfejs z pakietu `java.util.concurrent`, który pozwala na wykonywanie zadań:

* po określonym opóźnieniu,
* cyklicznie, w ustalonym interwale czasowym.

Jest to bardziej nowoczesna i bezpieczna alternatywa dla klasy `Timer`, szczególnie w aplikacjach wielowątkowych.

## ⚙️ Jak działa?

Zamiast tworzyć i zarządzać wątkami ręcznie, można delegować zadania do "executora", który automatycznie nimi zarządza. Planowanie odbywa się poprzez metody takie jak:

### 🔁 Najważniejsze metody

| Metoda                                                                                   | Opis                                                      |
| ---------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| `schedule(Runnable command, long delay, TimeUnit unit)`                                  | Uruchamia zadanie po określonym opóźnieniu                |
| `scheduleAtFixedRate(Runnable command, long initialDelay, long period, TimeUnit unit)`   | Uruchamia zadanie cyklicznie, w stałych odstępach czasu   |
| `scheduleWithFixedDelay(Runnable command, long initialDelay, long delay, TimeUnit unit)` | Uruchamia zadanie cyklicznie, po zakończeniu poprzedniego |

## 🧪 Przykład użycia

```java
import java.util.concurrent.*;

public class CacheRefresher {

    public static class RefreshTask implements Runnable {
        @Override
        public void run() {
            System.out.println("Odświeżam cache...");
            DictionaryCache.getInstance().reload();
        }
    }

    public static void main(String[] args) {
        ScheduledExecutorService scheduler = Executors.newScheduledThreadPool(1);

        Runnable task = new RefreshTask();
        scheduler.scheduleAtFixedRate(task, 0, 1, TimeUnit.MINUTES);
    }
}
```

## ✅ Zalety

* Lepsza obsługa wyjątków niż w klasie `Timer`
* Wielowątkowość — obsługuje wiele zadań równolegle
* Kontrola nad wątkami (można je zatrzymać, przerwać, skalować)

## 🧯 Zatrzymywanie

Aby zatrzymać executor:

```java
scheduler.shutdown();
```

Lub natychmiastowo:

```java
scheduler.shutdownNow();
```

## 🧠 Kiedy używać?

* Gdy trzeba cyklicznie wykonywać zadanie (np. odświeżanie cache)
* W aplikacjach serwerowych, backendowych (np. regularna synchronizacja)
* Zamiast ręcznego zarządzania wątkami dla prostszej i bezpieczniejszej kontroli

---

`ScheduledExecutorService` to nowoczesne narzędzie do planowania zadań — niezawodne, skalowalne i gotowe do użycia w środowiskach wielowątkowych. 🚀
