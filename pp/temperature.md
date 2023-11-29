---
layout: ../../layouts/Layout.astro
title: Temperature
---
```elm
type Temperature
    = Celsius Float
    | Kelvin Float
    | Fahrenheit Float

tempToCelsius : Temperature -> Temperature
tempToCelsius temp =
    case temp of
        Kelvin t ->
            Celsius (t - 273.1)

        Fahrenheit t ->
            Celsius ((t - 32) * (5 / 9))

        Celsius t ->
            Celsius t

compareTemperature : Temperature -> Temperature -> Float
compareTemperature temp1 temp2 =
    let
        cTemp1 =
            tempToCelsius temp1

        cTemp2 =
            tempToCelsius temp2
    in
    case ( cTemp1, cTemp2 ) of
        ( Celsius t1, Celsius t2 ) ->
            t1 - t2

        _ ->
            0
```
