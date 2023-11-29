---
layout: ../../layouts/Layout.astro
title: Aufgabe 03
---

```java
public class HalloCounter {
    public static void main(String[] args) {

        long a = 0;

        for (int i = 0; i < args.length; i++) {
            if (args[i].equals("Hallo")) {
                a += 1;
            }
        }

        System.out.println(a);
    }
}
```

 ```java
public class HalloX {
    public static void main(String[] args) {
        int a = 0;

        if (args.length == 0) {
            System.out.println("Bitte Argument eingeben!");
            System.exit(0);
        }

        try {
            a = Integer.parseInt(args[0]);
        } catch (NumberFormatException e) {
            System.out.println("Bitte nur ganze Zahlen als Argument eingeben");
            System.exit(0);
        }

        for (int i = 0; i < a; i++) {
            System.out.println("Hallo");
        }

    }
}
```

 ```java
 public class Dreieck {

    public static void main(String[] args) {

        int a = Integer.parseInt(args[0]);

        for (int i = a; i > 0; i--) {

            for (int j = a; j > 0; j--) {

                System.out.print("*");
            }

            System.out.print("\n");

            a--;
        }
    }
}
```