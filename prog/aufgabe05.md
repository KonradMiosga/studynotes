---
layout: ../../layouts/Layout.astro
title: Aufgabe 05
---
```java
public class Bruch {
    public static void main(String[] args) {
        if (args.length != 5) {
            System.out.println("Ungültige Menge an Argumenten!");
            System.out.println("Bsp: java Bruch add 1 2 3 4");
            System.exit(0);
        }
        int zaehler1 = Integer.parseInt(args[1]);
        int nenner1 = Integer.parseInt(args[2]);

        int zaehler2 = Integer.parseInt(args[3]);
        int nenner2 = Integer.parseInt(args[4]);

        int zaehler3 = 0;
        int nenner3 = 0;

        String operation = args[0];

        String operationSign = "";

        if (nenner1 == 0 || nenner2 == 0) {
            System.out.println("Nenner muss ungleich 0 sein!");
            System.exit(0);
        }

        switch (operation) {
            case "add":
                nenner3 = nenner1 * nenner2;
                zaehler3 = zaehler1 * nenner2 + zaehler2 * nenner1;
                operationSign = "+";
                break;
            case "sub":
                nenner3 = nenner1 * nenner2;
                zaehler3 = zaehler1 * nenner2 - zaehler2 * nenner1;
                operationSign = "-";
                break;
            case "mul":
                nenner3 = nenner1 * nenner2;
                zaehler3 = zaehler1 * zaehler2;
                operationSign = "*";
                break;
            case "div":
                nenner3 = nenner1 * zaehler2;
                zaehler3 = nenner2 * zaehler1;
                operationSign = "/";
                break;
            default:
                System.out.println("Ungültige Rechenoperation");
                System.out.println("add, sub, mul, div benutzen!");
                System.exit(0);
                break;

        }
        if (nenner3 < 0) {
            nenner3 = -nenner3;
            zaehler3 = -zaehler3;
        }
        System.out.printf("%d/%d %s %d/%d = %d/%d%n", zaehler1, nenner1, operationSign, zaehler2, nenner2, zaehler3,
                nenner3);

    }
}
```