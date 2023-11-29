---
layout: ../../layouts/Layout.astro
title: Date
---
```elm
type alias Date =
    { day : Int
    , month : Int
    , year : Int
    }


isLeapYear : Int -> Bool
isLeapYear n =
    if modBy 400 n /= 0 && modBy 100 n == 0 then
        False

    else if modBy 4 n == 0 then
        True

    else
        False


daysInMonth : Int -> Int -> Int
daysInMonth month year =
    case month of
        1 ->
            31

        2 ->
            if isLeapYear year then
                29

            else
                28

        3 ->
            31

        4 ->
            30

        5 ->
            31

        6 ->
            30

        7 ->
            31

        8 ->
            31

        9 ->
            30

        10 ->
            31

        11 ->
            30

        12 ->
            31

        _ ->
            0


tomorrow : Date -> Date
tomorrow date =
    if date.day < daysInMonth date.month date.year then
        { date | day = date.day + 1 }

    else if date.month < 12 then
        { date | day = 1, month = date.month + 1 }

    else
        { date | day = 1, month = 1, year = date.year + 1 }


yesterday : Date -> Date
yesterday date =
    if date.month == 1 then
        { date | day = 31, month = 12, year = date.year - 1 }

    else if date.day == 1 then
        { date | day = daysInMonth (date.month - 1) date.year, month = date.month - 1 }

    else
        { date | day = date.day - 1 }


compareDate : Date -> Date -> Int
compareDate date1 date2 =
    let
        d1 =
            date1.day

        m1 =
            date1.month

        y1 =
            date1.year

        d2 =
            date2.day

        m2 =
            date2.month

        y2 =
            date2.year

    in
    if y1 < y2 then
        -1

    else if y1 > y2 then
        1

    else if m1 < m2 then
        -1

    else if m1 > m2 then
        1

    else if d1 < d2 then
        -1

    else if d1 > d2 then
        1

    else
        0


addDays : Int -> Date -> Date
addDays n date =
    if n == 0 then
        date

    else if n > 0 then
        addDays (n - 1) (tomorrow date)

    else if n < 0 then
        addDays (n + 1) (yesterday date)

    else
        date


dateDifference : Date -> Date -> Int
dateDifference date1 date2 =
    if compareDate date1 date2 == 0 then
        0

    else if compareDate date1 date2 < 0 then
        1 + dateDifference (tomorrow date1) date2

    else
        1 + dateDifference (yesterday date1) date2


createDate : Int -> Int -> Int -> ( Date, Bool )
createDate y m d =
    let
        date : Date
        date =
            { day = d, month = m, year = y }
    in
    if tomorrow (yesterday date) == date && y >= 0 && m >= 0 && d >= 0 then
        ( date, True )

    else
        ( date, False )
```
