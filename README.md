# S14 - Kapselung / Packages / `private`

## Übung 1

Schreiben Sie eine Klasse `Date`, welche das Prinzip der Kapselung befolgt und die Kohärenz der Daten garantiert
(und wenn nötig eine Exception erzeugt). Gehen Sie von der Annahme aus, dass die Jahre immer 365 Tage umfassen (kein Schaltjahr).

``` java
public class Date {  // Spezifikation
    public Date(int day, int month) throws Exception;
    public int dayOfMonth();
    public int month();
}
```

> :exclamation: **Wichtig** : Das Standard-Toolkit der Bibliothek zur Verwaltung von Daten (z. B. `java.util.Calendar`) ist **nicht** verfügbar.

Schreiben Sie zwei verschiedene Implementationen dieser Klasse `Date`, **ohne irgendetwas** an der obenstehenden Deklaration (genau diese 3 Signaturen, alles andere ist `private`) **zu ändern**. Platzieren Sie die Klassen in zwei verschiedene Packungen mit Namen `s14.va` und `s14.vb`:

a) eine Variante mit zwei Ganzzahl-Attributen (Tag und Monat)<br/>
b) eine Variante mit einem einzigen Ganzzahl-Attribut (Nummer des Tages im Jahr [1..365])

Diese Übung ist wichtig für das Verständnis, dass die interne Repräsentation nicht zwingend Teil der Spezifikation ist. Der Benutzer der Klasse muss die Wahl der Implementation nicht kennen, so dass einige Daten ohne weiteres ausgetauscht werden können ohne das Verhalten der Komponente zu verändern.

Erstellen Sie danach in der Packung `s14.demo` zwei Klassen `DateDemoA` und `DateDemoB`.

Schreiben Sie anschliessend in diesen beiden Klassen eine Methode `main()` (mit für beide Varianten strikt identischem Rumpf), welche die Varianten a) und b) Ihrer Klasse `Date` testet, indem ein paar Daten erzeugt und die Resultate der beiden Methoden angezeigt werden.

Geben Sie **für jede Variante** je ein Argument, welches für die jeweilige Implementation spricht (in welchem Bezug ist eine Variante *besser* als die Andere?).

## Übung 2

Schreiben Sie eine Klasse `RationalNumber` zur Repräsentation von rationalen Zahlen mit den gemäß folgender Deklaration vorgesehenen Operationen (beachten Sie auch das Verwendungsbeispiel).

**Spezifikation:**

``` java
public class RationalNumber {
    public RationalNumber(int n, int d);

    public void    multiply(RationalNumber a);
    public void    divide  (RationalNumber a);
    public void    add     (RationalNumber a);
    public void    subtract(RationalNumber a);
    public void    multiply(int i);
    public void    add     (int i);
    public boolean lessThan(RationalNumber a);
    public boolean equals  (RationalNumber a);
    public float   toFloat ();
    public String  toString();
}
```

**Verwendungsbeispiel**

``` java
public class RationalNbDemo {

    public static void main(String[] args) {
        RationalNumber x, y;
        x = new RationalNumber(3, 4);
        y = new RationalNumber(9, 7);
        x.multiply(y);
        y.add(4);
        System.out.println("As float : " + x.toFloat());         // 0.9642
        System.out.println("As string: " + x.toString());        // "27/28"
        System.out.println(x + " = " + y + " ? " + x.equals(y));
        System.out.println(x + " < " + y + " ? " + x.lessThan(y));
    }
}
```

Beginnen Sie mit der Deklaration der Attribute und definieren Sie danach den Konstruktor und die Methodenrümpfe. **Eine Vereinfachung der Brüche ist nicht nötig**.

Wenn die Attribute als `private` deklariert sind, hat dann die Methode `add(RationalNumber a)` Zugriff auf die Attribute des Objektes `a` ?
