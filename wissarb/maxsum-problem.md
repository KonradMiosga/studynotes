---
layout: ../../layouts/Layout.astro
title: Maxsum-Problem 
---
Naiv:
```python
maxsum := A[0]
for i = 0 to n do
	for j = i to n do
		sum = 0
		for k = i to j do
			sum = sum + A[k]
		if sum > maxsum then
			maxsum = sum
return maxsum
```

So mittel:
```python
maxsum := A[0]
for i = 0 to n do
	sum = 0
	for j = i to n do
		sum = sum + A[j]
		if sum > maxsum then
			maxsum = sum
return maxsum
```

Magic:
```python
maxTemp := A[0]
maxSum := A[0]

for i = 1 to n do
	maxTemp = max(A[i], maxTemp + A[i])
	maxSum = max(maxSum, maxTemp)

return maxSum
```

## Korrektheit?
1. Es gibt *0 < i < j < n* , so dass die maximale Teilsumme in *A[i]* beginnt und in *A[j]* endet.
2. Algo "Magic" betrachtet für *0 < k < n* alle größten Teilfolgen, die bei *A[k]* enden, also auch die Folge *A[i] + ... + A[j]*.
