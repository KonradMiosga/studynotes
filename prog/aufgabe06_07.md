---
layout: ../../layouts/Layout.astro
title: Aufgabe 06/07
---
```java
public class Bruch2 {
  public static void main(String[] args) {

    if (args.length != 5) {
      System.out.println("Ungültige Menge an Argumenten!");
      System.out.println("Bsp: java Bruch add 1 2 3 4");
      System.exit(0);
    }
    int zaehler1 = Integer.parseInt(args[1]);
    int nenner1 = Integer.parseInt(args[2]);
    int[] bruch1 = { zaehler1, nenner1 };

    int zaehler2 = Integer.parseInt(args[3]);
    int nenner2 = Integer.parseInt(args[4]);
    int[] bruch2 = { zaehler2, nenner2 };

    String operation = args[0];

    String operationSign = "";

    if (nenner1 == 0 || nenner2 == 0) {
      System.out.println("Nenner muss ungleich 0 sein!");
      System.exit(0);
    }

    switch (operation) {
      case "add":
        operationSign = "+";
        System.out.println(mathToString(bruch1, bruch2, add(bruch1, bruch2), operationSign));
        break;
      case "sub":
        operationSign = "-";
        System.out.println(mathToString(bruch1, bruch2, sub(bruch1, bruch2), operationSign));
        break;
      case "mul":
        operationSign = "*";
        System.out.println(mathToString(bruch1, bruch2, mul(bruch1, bruch2), operationSign));
        break;
      case "div":
        operationSign = "/";
        System.out.println(mathToString(bruch1, bruch2, div(bruch1, bruch2), operationSign));
        break;

      default:
        break;

    }
  }

  public static String mathToString(int[] bruch1, int[] bruch2, int[] x,
      String operationSign) {

    String answer = "";
    answer = "" + bruch1[0] + "/" + bruch1[1] + " " + operationSign + " " + bruch2[0] + "/" + bruch2[1] + " = "
        + x[0]
        + "/" + x[1];
    return answer;
  }

  public static int[] add(int[] bruch1, int[] bruch2) {
    int x[] = new int[2];

    x[0] = bruch1[0] * bruch2[1] + bruch2[0] * bruch1[1];
    x[1] = bruch1[1] * bruch2[1];

    return kuerzen(x);
  }

  public static int[] sub(int[] bruch1, int[] bruch2) {
    int x[] = new int[2];

    x[0] = bruch1[0] * bruch2[0] - bruch2[1] * bruch1[0];
    x[1] = bruch1[1] * bruch2[1];

    return kuerzen(x);
  }

  public static int[] mul(int[] bruch1, int[] bruch2) {
    int x[] = new int[2];

    x[0] = bruch1[0] * bruch2[0];
    x[1] = bruch1[1] * bruch2[1];

    return kuerzen(x);

  }

  public static int[] div(int[] bruch1, int[] bruch2) {
    int x[] = new int[2];

    x[0] = bruch1[0] * bruch2[1];
    x[1] = bruch1[1] * bruch2[0];

    return kuerzen(x);
  }

  public static int euclid(int a, int b) {
    if (b == 0) {
      return a;
    }
    return euclid(b, a % b);
  }

  public static int[] kuerzen(int[] x) {
    int ggT = euclid(x[0], x[1]);
    x[0] = x[0] / ggT;
    x[1] = x[1] / ggT;

    if (x[1] < 0) {
      x[1] = x[1] * -1;
      x[0] = x[0] * -1;
    }
    return x;
  }
}
```

```java
public class BruchrechnerTest {
    public static void main(String[] args) {
        testAdd();

    }

    public static boolean annahmeGleich(int[] korrekt, int[] pruefen) {
        return ((korrekt[0] == pruefen[0]) && (korrekt[1] == pruefen[1]));

    }

    static void testAdd() {
        int[] bruch1 = new int[2];
        int[] bruch2 = new int[2];
        int[] ergebnisRichtig = new int[2];

        bruch1[0] = 1;
        bruch1[1] = 1;

        bruch2[0] = 1;
        bruch2[1] = 1;

        ergebnisRichtig[0] = 2;
        ergebnisRichtig[1] = 1;
        System.out.println(annahmeGleich(Bruch2.add(bruch1, bruch2), ergebnisRichtig));

        bruch1[0] = 1;
        bruch1[1] = 2;

        bruch2[0] = 1;
        bruch2[1] = 4;

        ergebnisRichtig[0] = 3;
        ergebnisRichtig[1] = 4;
        System.out.println(annahmeGleich(Bruch2.add(bruch1, bruch2), ergebnisRichtig));

        bruch1[0] = 3;
        bruch1[1] = -4;

        bruch2[0] = 1;
        bruch2[1] = 2;

        ergebnisRichtig[0] = -1;
        ergebnisRichtig[1] = 4;
        System.out.println(annahmeGleich(Bruch2.add(bruch1, bruch2), ergebnisRichtig));

        bruch1[0] = 3;
        bruch1[1] = -4;

        bruch2[0] = -1;
        bruch2[1] = 2;

        ergebnisRichtig[0] = -5;
        ergebnisRichtig[1] = 4;
        System.out.println(annahmeGleich(Bruch2.add(bruch1, bruch2), ergebnisRichtig));
    }

    static void testSub() {
        int[] bruch1 = new int[2];
        int[] bruch2 = new int[2];
        int[] ergebnisRichtig = new int[2];

        bruch1[0] = 1;
        bruch1[1] = 1;

        bruch2[0] = 1;
        bruch2[1] = 1;

        ergebnisRichtig[0] = 2;
        ergebnisRichtig[1] = 1;
        System.out.println(annahmeGleich(Bruch2.sub(bruch1, bruch2), ergebnisRichtig));
    }

//ab hier hatte ich scheinbar keine Lust mehr...
}
```