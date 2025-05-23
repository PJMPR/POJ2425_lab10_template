# ✨ Zadanie: Harmonogram Zadań

## 🌐 Cel projektu

Twoim celem jest stworzenie prostego systemu zarządzania harmonogramem zadań, który może być łatwo wykorzystany jako biblioteka w różnych projektach informatycznych.

## 🔧 Funkcjonalności biblioteki

Biblioteka powinna umożliwiać:

* ✏️ **Definiowanie zadań** poprzez interfejs `Job`, zawierający logikę wykonywanego zadania.
* ⏰ **Określanie harmonogramu** wykonania zadań:

  * kiedy rozpocząć,
  * co jaki czas powtarzać,
  * ile razy wykonać.
    Umożliwia to interfejs `JobScheduler` oraz jego implementacja `SimpleJobScheduler`.
* 🌌 **Reagowanie na upływ czasu** dzięki klasie `TimeEvent`, reprezentującej zdarzenia czasowe.
* 🚀 **Równoczesne wykonywanie zadań** – zadania i scheduler powinny działać w osobnych wątkach, zapewniając płynne działanie programu.

## 🔄 Wykorzystane wzorce projektowe

Projekt powinien wykorzystywać następujące wzorce:

* 🧰 **Singleton** – zapewnia istnienie tylko jednej instancji np. rejestru zadań.

  * → [Opis wzorca Singleton](https://refactoring.guru/pl/design-patterns/singleton)
* 🛡️ **Obserwator (Observer)** – umożliwia rejestrację zadań jako "nasłuchujących" zdarzeń czasowych.

  * → [Opis wzorca Obserwator](https://refactoring.guru/pl/design-patterns/observer)

---

Dobrze zaprojektowana biblioteka będzie stanowić solidną podstawę do dalszego rozszerzania i integracji z bardziej zaawansowanymi systemami.

