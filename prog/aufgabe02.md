---
layout: ../../layouts/Layout.astro
title: Aufgabe 02
---
```java
public class DivA {

    public static void main(String[] args) {

        byte byte1 = Byte.parseByte(args[0]);
        byte byte2 = Byte.parseByte(args[1]);

        long long1 = Long.parseLong(args[0]);
        long long2 = Long.parseLong(args[1]);

        double double1 = Double.parseDouble(args[0]);
        double double2 = Double.parseDouble(args[1]);

        System.out.println("Byte: " + byte1 / byte2);
        System.out.println("Long: " + long1 / long2);
        System.out.println("Double: " + double1 / double2);

    }
}
```

```java
public class DivB {

    public static void main(String[] args) {

        String a = "11111";
        String b = "333";

        int int1 = Integer.parseInt(a);
        int int2 = Integer.parseInt(b);

        float float1 = Float.parseFloat(a);
        float float2 = Float.parseFloat(b);

        double double1 = Double.parseDouble(a);
        double double2 = Double.parseDouble(b);

        System.out.println("Int: " + int1 / int2);
        System.out.println("Float: " + float1 / float2);
        System.out.println("Double: " + double1 / double2);

    }
}
```