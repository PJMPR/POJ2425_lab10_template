# 📏 Wzorzec projektowy: Builder & Fluent API

## 🌐 Opis ogólny

Wzorzec **Builder** (Budowniczy) to wzorzec konstrukcyjny, który pozwala krok po kroku tworzyć złożone obiekty. Zamiast wielkiego konstruktora z wieloma parametrami, używamy oddzielnej klasy (budowniczego), która umożliwia ustawianie wymaganych pól i ostateczne zbudowanie obiektu.

Często uzupełnia go technika **Fluent API**, która pozwala na łańcuchowe wywołania metod (method chaining) dzięki zwracaniu `this` z każdej metody konfiguracyjnej.

## 🔧 Zastosowanie

* Tworzenie obiektów z wieloma opcjonalnymi parametrami
* Zwiększenie czytelności kodu klienta
* Rozdzielenie procesu tworzenia od reprezentacji obiektu

## ⚖️ Składowe wzorca Builder

* **Builder**: interfejs/metoda z zestawem metod do konfigurowania obiektu
* **ConcreteBuilder**: implementacja budowniczego
* **Product**: tworzony obiekt
* **Director (opcjonalny)**: zarządza kolejnością wywołań buildera

## 🔄 Fluent API

Fluent API to styl projektowania interfejsu programistycznego, w którym:

* Metody zwracają obiekt `this`, co umożliwia ich łańcuchowanie
* Skupia się na czytelności i "naturalnym" wyglądzie kodu

### Przykład:

```java
JobScheduler scheduler = new JobSchedulerBuilder()
    .withJob(new PrintJob("Hello"))
    .everySeconds(2)
    .repeat(5)
    .build();
```

## 🔄 Przykładowa implementacja w Javie

```java
class JobSchedulerBuilder {
    private Job job;
    private int interval;
    private int repeatCount;

    public JobSchedulerBuilder withJob(Job job) {
        this.job = job;
        return this;
    }

    public JobSchedulerBuilder everySeconds(int seconds) {
        this.interval = seconds;
        return this;
    }

    public JobSchedulerBuilder repeat(int count) {
        this.repeatCount = count;
        return this;
    }

    public JobScheduler build() {
        return new JobScheduler(job, interval, repeatCount);
    }
}
```

## 🔍 Zalety

* Klarowny, czytelny i zrozumiały kod
* Oddzielenie konstrukcji od reprezentacji
* Eliminacja długich list parametrów w konstruktorach

## 🚫 Wady

* Więcej klas (nadmiar kodu przy prostych obiektach)
* Możliwość niepoprawnego użycia, jeśli nie ma walidacji

## 🚀 Podsumowanie

Wzorzec Builder z Fluent API to skuteczny sposób na tworzenie obiektów w złożonych konfiguracjach. W kontekście projektu harmonogramu pozwala intuicyjnie i elastycznie definiować, jak i kiedy zadanie ma być wykonane.
