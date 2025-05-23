# 📄 Odczyt plików CSV w Javie

## 🔍 Czym jest plik CSV?

Plik CSV (*Comma-Separated Values*) to prosty format tekstowy, w którym dane są rozdzielone przecinkami lub innymi separatorami (np. średnikiem `;`). Jest to popularny sposób przechowywania danych tabelarycznych.

## 🔧 Odczyt CSV za pomocą klasy `Scanner`

Możesz także użyć klasy `Scanner`, która umożliwia prosty i szybki odczyt plików CSV.

### 🧪 Przykład:

```java
import java.io.File;
import java.io.FileNotFoundException;
import java.util.*;

public class ScannerCsvReader {

    public List<String[]> readCsv(String filePath) throws FileNotFoundException {
        List<String[]> data = new ArrayList<>();
        Scanner scanner = new Scanner(new File(filePath));

        while (scanner.hasNextLine()) {
            String line = scanner.nextLine();
            String[] fields = line.split(",");
            data.add(fields);
        }

        scanner.close();
        return data;
    }
}
```

`Scanner` dobrze sprawdza się przy prostych plikach, ale nie radzi sobie z bardziej złożonymi przypadkami (np. przecinki w cudzysłowie).

---

## 🔧 Odczyt CSV za pomocą standardowych klas Javy

Java nie posiada wbudowanej dedykowanej klasy do CSV, ale można łatwo to zaimplementować przy użyciu `BufferedReader` i `String.split()`:

### 🧪 Przykład:

```java
import java.io.*;
import java.util.*;

public class SimpleCsvReader {
    public List<String[]> read(String filePath) throws IOException {
        List<String[]> result = new ArrayList<>();
        try (BufferedReader br = new BufferedReader(new FileReader(filePath))) {
            String line;
            while ((line = br.readLine()) != null) {
                String[] values = line.split(",");
                result.add(values);
            }
        }
        return result;
    }
}
```

## 📦 Odczyt CSV z użyciem biblioteki `opencsv`

Do bardziej zaawansowanego przetwarzania CSV warto użyć biblioteki [OpenCSV](http://opencsv.sourceforge.net/):

### 🛠️ Dodanie do projektu (Maven)

Aby użyć tej biblioteki, należy dodać ją do pliku `pom.xml` znajdującego się w katalogu głównym projektu Maven.

Wewnątrz znacznika `<dependencies>` dodaj wpis:

Do bardziej zaawansowanego przetwarzania CSV warto użyć biblioteki [OpenCSV](http://opencsv.sourceforge.net/):

### 🧰 Dodanie do projektu (Maven)

```xml
<dependency>
    <groupId>com.opencsv</groupId>
    <artifactId>opencsv</artifactId>
    <version>5.8</version>
</dependency>
```

### 🧪 Przykład z mapowaniem danych (OpenCSV)

Możesz również odczytać plik CSV i automatycznie mapować jego zawartość na obiekty klasy Java przy użyciu adnotacji `@CsvBindByName`:

#### 📦 Klasa modelu danych:

```java
import com.opencsv.bean.CsvBindByName;

public class DictionaryValue {

    @CsvBindByName(column = "ID")
    private int id;

    @CsvBindByName(column = "IntKey")
    private int intKey;

    @CsvBindByName(column = "StringKey")
    private String stringKey;

    @CsvBindByName(column = "EnumerationName")
    private String name;

    @CsvBindByName(column = "Value")
    private String value;

    // Gettery i settery...
}
```

#### 📘 Klasa czytająca dane:

```java
import com.opencsv.bean.CsvToBean;
import com.opencsv.bean.CsvToBeanBuilder;
import java.io.FileReader;
import java.util.List;

public class DictionaryCsvReader {
    public List<DictionaryValue> readCsv(String filePath) throws Exception {
        try (FileReader reader = new FileReader(filePath)) {
            CsvToBean<DictionaryValue> csvToBean = new CsvToBeanBuilder<DictionaryValue>(reader)
                .withType(DictionaryValue.class)
                .withIgnoreLeadingWhiteSpace(true)
                .build();
            return csvToBean.parse();
        }
    }
}
```

Upewnij się, że nagłówki w pliku CSV dokładnie odpowiadają nazwom określonym w adnotacjach `@CsvBindByName`.

## ✅ Kiedy wybrać bibliotekę zewnętrzną?

* Gdy dane zawierają pola z przecinkami lub znakami cudzysłowu
* Gdy wymagane jest mapowanie danych na obiekty (np. `@CsvBindByName` w OpenCSV)
* Przy dużych plikach, złożonych danych lub wymaganej walidacji

## 📚 Inne popularne biblioteki

* **Apache Commons CSV** (`org.apache.commons:commons-csv`)
* **uniVocity-parsers** — bardzo szybka i wydajna

---

Odczyt plików CSV w Javie można zrealizować zarówno prostymi środkami, jak i z pomocą dedykowanych frameworków. Wybierz podejście w zależności od złożoności danych i wymagań projektu. 📊
