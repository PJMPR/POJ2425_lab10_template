# 📚 Podstawowe Metody Klasy `String` w Javie

W Javie `String` to jedna z najczęściej używanych klas. Reprezentuje niezmienny (immutable) ciąg znaków. Poniżej znajduje się zestawienie najważniejszych metod, które warto znać na początku nauki.

---

## ✨ Tworzenie Stringów

```java
String tekst = "Witaj świecie!";
String pusty = new String();         // pusty string
String zTablicy = new String(new char[] {'J', 'a', 'v', 'a'});
```

---

## 🔍 Najczęściej używane metody

### `length()`

📏 Zwraca długość łańcucha znaków.

```java
int dlugosc = tekst.length(); // np. 14
```

---

### `charAt(int index)`

🔠 Zwraca znak znajdujący się na danej pozycji (indeks od 0).

```java
char znak = tekst.charAt(0); // 'W'
```

---

### `substring(int beginIndex, int endIndex)`

✂️ Zwraca fragment tekstu od `beginIndex` do `endIndex` (bez niego).

```java
String fragment = tekst.substring(6, 13); // "świecie"
```

---

### `equals(String other)` i `equalsIgnoreCase(String other)`

📌 Porównuje dwa napisy (z uwzględnieniem lub bez wielkości liter).

```java
tekst.equals("Witaj świecie");       // false
tekst.equalsIgnoreCase("witaj ŚWIECIE!"); // true
```

---

### `contains(String sequence)`

🔍 Sprawdza, czy napis zawiera daną sekwencję znaków.

```java
boolean zawiera = tekst.contains("świat"); // true
```

---

### `startsWith(String prefix)` / `endsWith(String suffix)`

🏁 Sprawdza, czy napis zaczyna się lub kończy na daną frazę.

```java
tekst.startsWith("Witaj"); // true
tekst.endsWith("!");       // true
```

---

### `toUpperCase()` / `toLowerCase()`

🔡 Zmienia wielkość liter.

```java
tekst.toUpperCase(); // "WITAJ ŚWIECIE!"
tekst.toLowerCase(); // "witaj świecie!"
```

---

### `trim()`

✂️ Usuwa białe znaki z początku i końca ciągu znaków.

```java
String tekstZSpacjami = "  Hello  ";
tekstZSpacjami.trim(); // "Hello"
```

---

### `replace(CharSequence target, CharSequence replacement)`

🔁 Zamienia wszystkie wystąpienia ciągu znaków na inne.

```java
tekst.replace("Witaj", "Hello"); // "Hello świecie!"
```

---

### `split(String regex)`

🔨 Dzieli ciąg znaków na części wg wzorca (np. spacji lub przecinka).

```java
String[] slowa = tekst.split(" "); // ["Witaj", "świecie!"]
```

---

### `isEmpty()` / `isBlank()` (od Javy 11)

✅ Sprawdza, czy string jest pusty lub zawiera tylko białe znaki.

```java
"".isEmpty();    // true
"  ".isBlank();  // true
```

---

## 🧠 Wskazówki

- `String` jest niemutowalny – operacje na nim tworzą nowy obiekt.
- Do częstych modyfikacji tekstu warto używać `StringBuilder`.

---

To tylko początek – `String` w Javie oferuje wiele innych przydatnych metod. Zachęcam do eksploracji dokumentacji Javy i samodzielnego testowania kodu! 🚀
