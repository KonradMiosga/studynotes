---
layout: ../../layouts/Layout.astro
title: Tupel
---
# Tupel
```elm
nestedPair : Float
nestedPair =
    ( "hello", ( ( 3.0, "my" ), "dear" ) )
        |> Tuple.second
        |> Tuple.first
        |> Tuple.first


rotate : Float -> ( Float, Float ) -> ( Float, Float )
rotate angle vector =
    let
        theta =
            degrees angle

        x =
            Tuple.first vector

        y =
            Tuple.second vector
    in
    ( x * cos theta - y * sin theta, x * sin theta + y * cos theta )


innerProduct : ( Float, Float ) -> ( Float, Float ) -> Float
innerProduct firstVec secondVec =
    Tuple.first firstVec * Tuple.first secondVec + Tuple.second firstVec * Tuple.second secondVec


vectorFromTo : ( Float, Float ) -> ( Float, Float ) -> ( Float, Float )
vectorFromTo p q =
    ( Tuple.first q - Tuple.first p, Tuple.second q - Tuple.second p )


leftRightOrOn : ( ( Float, Float ), ( Float, Float ) ) -> ( Float, Float ) -> Int
leftRightOrOn ( p, q ) v =
    let
        skalar =
            innerProduct (rotate 90 (vectorFromTo q p)) (vectorFromTo v p)
    in
    if skalar < 0 then
        -1

    else if skalar > 0 then
        1

    else
        0


insideTriangle : ( Float, Float ) -> ( Float, Float ) -> ( Float, Float ) -> ( Float, Float ) -> Bool
insideTriangle p q r v =
    if (leftRightOrOn ( p, q ) v + leftRightOrOn ( q, r ) v + leftRightOrOn ( r, p ) v) == 3 then
        True

    else
        False
```
