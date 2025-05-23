# 🛡️ Wzorzec projektowy: Obserwator (Observer)

## 🌐 Opis ogólny

Wzorzec **Obserwator** (ang. *Observer*) jest wzorcem behawioralnym, który definiuje zależność jeden-do-wielu pomiędzy obiektami. Gdy jeden obiekt (zwany *podmiotem*, ang. *Subject*) zmienia swój stan, wszystkie jego zależne obiekty (*obserwatorzy*, ang. *Observers*) są automatycznie powiadamiane i aktualizowane.

## 📅 Zastosowanie

Wzorzec ten znajduje zastosowanie wszędzie tam, gdzie zmiana stanu jednego obiektu powinna prowadzić do powiadomienia innych komponentów, np.:

* interfejsy graficzne (GUI)
* systemy powiadomień
* zdarzenia czasowe i planowanie zadań (jak w naszym projekcie)
* synchronizacja danych

## ⚖️ Składowe wzorca

* **Subject (Podmiot)**: obiekt, który przechowuje listę obserwatorów i informuje ich o zmianach stanu.
* **Observer (Obserwator)**: interfejs lub klasa, która definiuje metodę aktualizacji (np. `update()`), wywoływaną przez `Subject`.
* **ConcreteSubject**: implementacja `Subject`, która przechowuje konkretny stan i informuje obserwatorów o zmianach.
* **ConcreteObserver**: implementacja `Observer`, która reaguje na zmiany stanu `Subject`.

## 📈 Diagram UML

```
+----------------+          +------------------+
|   Subject      |<>------->|   Observer       |
+----------------+          +------------------+
| +attach()      |          | +update()        |
| +detach()      |          +------------------+
| +notify()      |                /\
+----------------+                 |
      /\                            |
       |                            |
       |                    +--------------------+
       |                    | ConcreteObserver   |
+-------------------+       +--------------------+
| ConcreteSubject   |
+-------------------+
| -state            |
| +getState()       |
| +setState()       |
+-------------------+
```

## 🔄 Przykład w Javie

```java
interface Observer {
    void update(String message);
}

class ConcreteObserver implements Observer {
    private String name;
    public ConcreteObserver(String name) {
        this.name = name;
    }
    public void update(String message) {
        System.out.println(name + " otrzymał: " + message);
    }
}

class Subject {
    private List<Observer> observers = new ArrayList<>();

    public void attach(Observer o) {
        observers.add(o);
    }

    public void detach(Observer o) {
        observers.remove(o);
    }

    public void notifyObservers(String msg) {
        for (Observer o : observers) {
            o.update(msg);
        }
    }
}
```

## 🔍 Korzyści

* Luźnie powiązanie między komponentami
* Łatwa rozbudowa o nowych obserwatorów
* Skalowalność i elastyczność

## 🚫 Wady

* Możliwość nieoczekiwanych aktualizacji lub pętli, jeśli obserwatorzy wzajemnie się powiadamiają
* Trudniejsza analiza zależności w dużych systemach

## 🚀 Podsumowanie

Wzorzec Obserwator jest świetnym rozwiązaniem wszędzie tam, gdzie chcemy stworzyć system zdarzeniowy z dynamiczną liczbą odbiorców zmian. W projekcie harmonogramu zadań pozwala on schedulerom reagować na zdarzenia czasowe generowane przez zegar.
