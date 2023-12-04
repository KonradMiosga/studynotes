---
layout: ../../layouts/Layout.astro
title: Aufgabe 08
---
```java
class Pony {
    String name;
    
    Pony(String name) {
        this.name = name;
    }

    void feed() {
        System.out.println(name + " got some food");
    }
    void pet() {
        System.out.println(name + " was petted");
    }
}
```

```java
class Ponyhof {
    Pony[] ponies;
    int ponyCount = 0;

    Ponyhof(int size) {
        ponies = new Pony[size];
    }

    void add(Pony pony) {
        System.out.println("Trying to add: " + pony.name);
        for (int i = 0; i < ponies.length; i++) {
            if (ponies[i] == null) {
                ponies[i] = pony;
                ponyCount++;
                System.out.println("...added");
                return;
            }
        }
        System.out.println("Not enough room!");
    }

    void remove(Pony pony) {
        for (int i = 0; i < ponies.length; i++) {
            if (pony.equals(ponies[i])) {
                ponies[i] = null;
                ponyCount--;
                System.out.println(pony.name + " is no more. :(");
                return;
            }
        }
        System.out.println(pony.name + " was never in there.");
    }

    void countPonies() {
        int newPonyCount = 0;
        for (Pony pony : ponies) {
            if (pony != null) {
                newPonyCount++;
            }
        }
        ponyCount = newPonyCount;
    }

    void feedAll() {
        for (int i = 0; i < ponies.length; i++) {
            if (ponies[i] != null) {
                ponies[i].feed();
            }
        }
    }

    void petAll() {
        for (int i = 0; i < ponies.length; i++) {
            if (ponies[i] != null) {
                ponies[i].pet();
            }
        }
    }

    void growTo(int newSize) {
        if (newSize > ponies.length) {
            Pony[] newPonies = new Pony[newSize];
            for (int i = 0; i < ponies.length; i++) {
                newPonies[i] = ponies[i];
            }
            ponies = newPonies;
            countPonies();
            System.out.println("Ponyhof resized to " + newSize);
        } else if (newSize >= ponyCount) {
            System.out.println("New size should be greater than the current size.");
        }
    }

    void displayPonies() {
        System.out.println("Your current Ponyhof:");
        System.out.println("Filled spaces: " + ponyCount + " Empty spaces: " + (ponies.length - ponyCount));
        for (int i = 0; i < ponies.length; i++) {
            if (ponies[i] != null) {
                System.out.println((i + 1) + ". " + ponies[i].name);
            } else {
                System.out.println((i + 1) + ". Empty space");
            }
        }
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        Ponyhof myPonyhof = new Ponyhof(5);

        Pony amber = new Pony("Amber");
        Pony bliss = new Pony("Bliss");
        Pony crystal = new Pony("Crystal");
        Pony dandelion = new Pony("Dandelion");
        Pony everglow = new Pony("Everglow");
        Pony foxy = new Pony("Foxy");

        myPonyhof.displayPonies();
        System.out.println("");
        
        System.out.println("Adding some ponies:");
        myPonyhof.add(amber);
        myPonyhof.add(bliss);
        myPonyhof.add(crystal);
        myPonyhof.add(dandelion);
        myPonyhof.add(everglow);
        System.out.println("");

        myPonyhof.displayPonies();
        System.out.println("");

        System.out.println("Trying to add a pony, but there isn't enough space.");
        myPonyhof.add(foxy);
        System.out.println("");

        System.out.println("Feed all the ponies.");
        myPonyhof.feedAll();
        System.out.println("");

        System.out.println("Remove one pony.");
        myPonyhof.remove(bliss);
        System.out.println("");

        myPonyhof.displayPonies();
        System.out.println("");
        
        System.out.println("Trying to remove a pony, that isn't in the there.");
        myPonyhof.remove(foxy);
        System.out.println("");

        System.out.println("Adding a new pony.");
        myPonyhof.add(foxy);
        System.out.println("");

        myPonyhof.displayPonies();
        System.out.println("");

        System.out.println("Pet all the ponies.");
        myPonyhof.petAll();
        System.out.println("");
        
        System.out.println("Trying to increase Ponyhof to 6 spaces.");
        myPonyhof.growTo(6);
        System.out.println("");
        
        myPonyhof.displayPonies();
        System.out.println("");

        myPonyhof.add(bliss);
        System.out.println("");

        myPonyhof.displayPonies();
        System.out.println("");

        myPonyhof.petAll();
        System.out.println("");

        myPonyhof.displayPonies();
        System.out.println("");

        System.out.println("Remove one pony.");
        myPonyhof.remove(amber);
        System.out.println("");

        myPonyhof.displayPonies();
        System.out.println("");
    }
}
```
