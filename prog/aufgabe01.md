---
layout: ../../layouts/Layout.astro
title: Aufgabe 01
---
```java
public class Hello {
    public static void main (String [] args) {

        System.out.println("Hello World!");
    }
}
```

```java
public class Echo {
    public static void main(String[] args) {
        if (args.length > 0) {
            for (int i = 0; i < args.length; i++) {
                System.out.print(args[i] + " ");
            }
            System.out.print("\n");
        }
    }
}
```