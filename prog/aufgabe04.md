---
layout: ../../layouts/Layout.astro
title: Aufgabe 04
---
```java
import java.util.Random;

public class Array {

    public static void main(String[] args) {

        int size = 5;

        int min;

        int max;

        float mid;

        int median = 0;

        int sum = 0;

        int[] myArray = new int[size];

        Random rand = new Random();

        for (int i = 0; i < size; i++) {

            myArray[i] = rand.nextInt(10) + 1;
            System.out.print(myArray[i] + " ");
        }
        System.out.println(" ");
        min = max = myArray[0];

        for (int i = 0; i < size; i++) {
            // find min and max
            if (myArray[i] < min)
                min = myArray[i];
            if (myArray[i] > max)
                max = myArray[i];

            // sum for mean
            sum += myArray[i];

        }

        System.out.println("Minimum: " + min);
        System.out.println("Maximum: " + max);

        // calc mean
        mid = (float) sum / size;
        System.out.println("Arithmetisches Mittel: " + mid);

        // wild median magic
        for (int i = 0; i < size; i++) {
            int pivot = myArray[i];
            int smaller = 0;
            int bigger = 0;

            for (int j = 0; j < size; j++) {
                if (i == j)
                    continue; // don't compare to yourself, dummy!
                if (pivot <= myArray[j])
                    smaller++;
                if (pivot >= myArray[j])
                    bigger++;
            }

            if (smaller == bigger || 
	            smaller == bigger + 1 || 
	            smaller == bigger - 1) {
                
                median = myArray[i];
                break;
            }
        }

        System.out.println("Median: " + median);
    }
}
```