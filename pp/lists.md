---
layout: ../../layouts/Layout.astro
title: Lists
---

```elm
module Lists exposing (..)

import Date exposing (..)


range : Int -> Int -> List Int
range a b =
    if a > b then
        rangeFwd a b

    else
        rangeBckwd a b


rangeFwd : Int -> Int -> List Int
rangeFwd a b =
    if a > b then
        []

    else
        a :: rangeFwd (a + 1) b


rangeBckwd : Int -> Int -> List Int
rangeBckwd a b =
    if a < b then
        []

    else
        a :: rangeBckwd (a - 1) b


repeat : Int -> String -> List String
repeat howOften what =
    if howOften <= 0 then
        []

    else
        what :: repeat (howOften - 1) what


datesFromTo : Date -> Date -> List Date
datesFromTo dayFrom dayTo =
    if dayFrom == dayTo then
        [ dayTo ]

    else
        dayFrom :: datesFromTo (tomorrow dayFrom) dayTo


isPrime : Int -> Bool
isPrime n =
    primeHelper n (n - 1)


primeHelper : Int -> Int -> Bool
primeHelper a b =
    if b <= 1 then
        True

    else if modBy b a == 0 then
        False

    else
        primeHelper a (b - 1)


primesFromTo : Int -> Int -> List Int
primesFromTo a b =
    if a > b then
        []

    else if isPrime a then
        a :: primesFromTo (a + 1) b

    else
        primesFromTo (a + 1) b


primesUntil : Int -> List Int
primesUntil n =
    primesFromTo 2 n


countPrimesUntil : Int -> Int
countPrimesUntil n =
    let
        sumList a =
            case a of
                [] ->
                    0

                x :: xs ->
                    x + sumList xs
    in
    sumList (primesUntil n)


laenge : List a -> Int
laenge list =
    case list of
        [] ->
            0

        _ :: restList ->
            1 + laenge restList


incrementAll : List Int -> List Int
incrementAll list =
    case list of
        [] ->
            []

        x :: xs ->
            (x + 1) :: incrementAll xs


kleinbuchstaben : String -> String
kleinbuchstaben wort =
    String.fromList (kleinbuchstabenHelper (String.toList wort))


kleinbuchstabenHelper : List Char -> List Char
kleinbuchstabenHelper charList =
    case charList of
        [] ->
            []

        c :: cs ->
            Char.toLower c :: kleinbuchstabenHelper cs


toAltCaps : String -> String
toAltCaps worte =
    String.fromList (toAltHelper (String.toList worte))


toAltHelper : List Char -> List Char
toAltHelper charList =
    case charList of
        a :: b :: restList ->
            Char.toUpper a :: Char.toLower b :: toAltHelper restList

        [ c ] ->
            [ Char.toUpper c ]

        [] ->
            []


append : List a -> List a -> List a
append list1 list2 =
    case list1 of
        [] ->
            list2

        x :: rest ->
            x :: append rest list2


umdrehen : List a -> List a
umdrehen list =
    case list of
        [] ->
            []

        x :: xs ->
            append (umdrehen xs) [ x ]


erzeugenHelp : Int -> Int -> List Int
erzeugenHelp a b =
    if a > (b - 1) then
        []

    else
        a :: erzeugenHelp (a + 1) b


erzeugen : Int -> List Int
erzeugen a =
    erzeugenHelp 0 a


erzeugenUndUmdrehen : Int -> Int
erzeugenUndUmdrehen list =
    list |> erzeugen |> umdrehen |> laenge


insertIntoSorted : Int -> List Int -> List Int
insertIntoSorted n list =
    case list of
        a :: restList ->
            if n < a then
                n :: a :: restList

            else
                a :: insertIntoSorted n restList

        [] ->
            [ n ]


insertionSort : List Int -> List Int
insertionSort list =
    case list of
        [] ->
            []

        a :: restList ->
            insertIntoSorted a (insertionSort restList)


reverse : List a -> List a
reverse listig =
    let
        reverse2 : List a -> List a -> List a
        reverse2 listSoFar list =
            case ( listSoFar, list ) of
                ( [], [] ) ->
                    []

                ( ys, [] ) ->
                    ys

                ( ys, x :: xs ) ->
                    reverse2 (x :: ys) xs
    in
    reverse2 [] listig


listenLaenge : List a -> Int
listenLaenge listig =
    let
        listenLaengeHelp : Int -> List a -> Int
        listenLaengeHelp acc list =
            case ( acc, list ) of
                ( a, [] ) ->
                    a

                ( a, _ :: xs ) ->
                    listenLaengeHelp (a + 1) xs
    in
    listenLaengeHelp 0 listig


listeVonBisHelp : Int -> Int -> List Int -> List Int
listeVonBisHelp a b listSoFar =
    if a > b then
        listSoFar

    else
        listeVonBisHelp (a + 1) b (append listSoFar [ a ])


listeVonBis : Int -> Int -> List Int
listeVonBis a b =
    listeVonBisHelp a b []


applyToEach : (a -> b) -> List a -> List b
applyToEach f listig =
    let
        applyToEach2 : (a -> b) -> List b -> List a -> List b
        applyToEach2 func listSoFar list =
            case list of
                [] ->
                    reverse listSoFar

                x :: xs ->
                    applyToEach2 func (f x :: listSoFar) xs
    in
    applyToEach2 f [] listig


keepOnlyThoseWith : (a -> Bool) -> List a -> List a
keepOnlyThoseWith f list =
    let
        keepOnlyThoseWith2 : (a -> Bool) -> List a -> List a -> List a
        keepOnlyThoseWith2 func listSoFar listig =
            case listig of
                [] ->
                    reverse listSoFar

                x :: xs ->
                    if func x == True then
                        keepOnlyThoseWith2 func (x :: listSoFar) xs

                    else
                        keepOnlyThoseWith2 func listSoFar xs
    in
    keepOnlyThoseWith2 f [] list


labelAsPrime : List Int -> List ( Int, Bool )
labelAsPrime list =
    let
        labelOneNumber : Int -> ( Int, Bool )
        labelOneNumber n =
            ( n, isPrime n )
    in
    applyToEach labelOneNumber list


addAll2 : Int -> List Int -> Int
addAll2 start list =
    case list of
        [] ->
            start

        x :: rest ->
            addAll2 (start + x) rest


combineAll : (a -> b -> b) -> b -> List a -> b
combineAll f start list =
    let
        combAllHelp : (a -> b -> b) -> b -> List a -> b
        combAllHelp func startH listH =
            case listH of
                [] ->
                    startH

                x :: restH ->
                    combAllHelp func (func x startH) restH
    in
    combAllHelp f start (reverse list)


combineAll2 : (a -> b -> b) -> b -> List a -> b
combineAll2 f start list =
    case list of
        [] ->
            start

        x :: rest ->
            combineAll2 f (f x start) rest


comb : Int -> Int -> Int
comb x s =
    x + 10 * s


leftToRightMaxima : List Int -> List Int
leftToRightMaxima list =
    let
        foo : Int -> ( List Int, Int ) -> ( List Int, Int )
        foo currentElement ( result, maxValue ) =
            if currentElement >= maxValue then
                ( currentElement :: result, currentElement )

            else
                ( result, maxValue )
    in
    List.reverse (Tuple.first (List.foldl foo ( [], 0 ) list))


numberItems : Int -> List String -> List ( Int, String )
numberItems startIdx list =
    let
        foo x ( acc, idx ) =
            ( ( idx, x ) :: acc, idx + 1 )
    in
    List.foldl foo ( [], startIdx ) list |> Tuple.first |> List.reverse




mapWithFold : (a -> b) -> List a -> List b
mapWithFold f list =
    List.foldr (\x acc -> f x :: acc) [] list


filterWithFold : (a -> Bool) -> List a -> List a
filterWithFold f list =
    let
        foo x acc =
            if f x then
                x :: acc

            else
                acc
    in
    List.foldr foo [] list


loop : Int -> (a -> b) -> a -> b
loop n f x =
    case n of
        1 ->
            f x

        _ ->
            loop (n - 1) f x

```
