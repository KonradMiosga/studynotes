---
layout: ../../layouts/Layout.astro
title: Rekursion
---
```elm
factorial : Int -> Int
factorial n =
    if n == 0 then
        1

    else
        n * factorial (n - 1)


sumOfSquaresUpTo : Int -> Int
sumOfSquaresUpTo n =
    if n == 1 then
        1

    else
        n ^ 2 + sumOfSquaresUpTo (n - 1)


collatz : Int -> Int
collatz n =
    if modBy 2 n == 0 then
        n // 2

    else
        3 * n + 1


collatzUntilOne : Int -> Int
collatzUntilOne n =
    if n == 1 then
        0

    else
        1 + collatzUntilOne (collatz n)


squareRoot : Int -> Int -> Int
squareRoot n k =
    if k == 1 then
        1

    else if k ^ 2 <= n then
        k

    else
        squareRoot n (k - 1)


fib : Int -> Int
fib n =
    case n of
        0 ->
            0

        1 ->
            1

        _ ->
            fib (n - 2) + fib (n - 1)


weird : Int -> Int
weird n =
    if n == 0 then
        0

    else if n >= 1 && modBy 2 (weird (n - 1)) == 1 then
        n + weird (n - 1)

    else
        weird (n - 1) // 2 + 1


weirdHelper : Int -> Int -> Int
weirdHelper wNminus1 n =
    if modBy 2 wNminus1 == 1 then
        wNminus1 + n

    else
        wNminus1 // 2 + 1


weirdWithHelper : Int -> Int
weirdWithHelper n =
    if n == 0 then
        0

    else
        weirdHelper (weirdWithHelper (n - 1)) n
```
