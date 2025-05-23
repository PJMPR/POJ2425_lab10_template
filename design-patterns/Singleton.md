# 🧩 Wzorzec projektowy: Singleton (Java)

## 🔍 Czym jest Singleton?

Singleton to wzorzec projektowy z grupy wzorców kreacyjnych. Jego zadaniem jest zapewnienie, że klasa posiada tylko **jedną instancję**, do której dostęp jest możliwy globalnie.

W tym projekcie, Singleton wykorzystywany jest np. w klasie `DictionaryCache`, aby zapewnić współdzielony i spójny dostęp do cache danych słownikowych.

## 🛠️ Implementacja w stylu projektu

Kod poniżej odpowiada implementacji z pliku `SingletonExample.java`:

```java
public class SingletonExample {

    // 🛑 Prywatny konstruktor — uniemożliwia tworzenie instancji spoza klasy
    private SingletonExample() {
    }

    // 📦 Statyczne pole przechowujące jedyną instancję
    private static SingletonExample instance;

    // 🔁 Publiczna metoda dostępu z synchronizacją (bezpieczna dla wielu wątków)
    public static synchronized SingletonExample getInstance() {
        if (instance == null) instance = new SingletonExample();
        return instance;
    }
}
```

## 🔐 Bezpieczeństwo wielowątkowe

W powyższej implementacji zastosowano `synchronized`, aby zapobiec wyścigom w środowisku wielowątkowym. Dzięki temu tylko jeden wątek może utworzyć instancję klasy, a inne muszą poczekać.

## 📚 Zastosowanie w projekcie

* Klasa `DictionaryCache` powinna działać w analogiczny sposób,
* Jedna instancja Cache zapewnia spójny dostęp do danych w całej aplikacji,
* Idealne rozwiązanie do zarządzania wspólnymi zasobami.

## ⚠️ Uwaga na nadużycia

Singleton może komplikować testowanie (np. testy jednostkowe), dlatego warto stosować go tylko wtedy, gdy rzeczywiście potrzebna jest **globalna pojedyncza instancja**.

---

Zastosowanie wzorca Singleton to jeden z fundamentów tego projektu. Rozumienie jego działania ułatwi Ci projektowanie solidnych i bezpiecznych aplikacji wielowątkowych ☕
