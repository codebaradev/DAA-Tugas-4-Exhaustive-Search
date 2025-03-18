# Tugas Exhaustive Search

### Nomor 1

![Algorithm Diagram](assets/soal-1.png)

jawaban:

```
n = 4

C = 4!
  = 4 x 3 x 2 x 1
  = 24 
```

ada 24 kemungkinan kombinasi yang terbentuk, berikut kombinasinya yang terbentuk.


| No | Kombinasi (Orang → Job) | Perhitungan Biaya | Total Biaya |
|----|--------------------------|--------------------|------------|
| 1.  | (1, 2, 3, 4)  | 9 + 4 + 1 + 4  | **18** |
| 2.  | (1, 2, 4, 3)  | 9 + 4 + 4 + 9  | **26** |
| 3.  | (1, 3, 2, 4)  | 9 + 8 + 3 + 4  | **24** |
| 4.  | (1, 3, 4, 2)  | 9 + 8 + 9 + 7  | **33** |
| 5.  | (1, 4, 2, 3)  | 9 + 6 + 3 + 4  | **22** |
| 6.  | (1, 4, 3, 2)  | 9 + 6 + 1 + 7  | **23** |
| 7.  | (2, 1, 3, 4) -> Terkecil | 6 + 2 + 1 + 4  | **13** |
| 8.  | (2, 1, 4, 3)  | 6 + 2 + 9 + 4  | **21** |
| 9.  | (2, 3, 1, 4)  | 6 + 8 + 7 + 4  | **25** |
| 10. | (2, 3, 4, 1)  | 6 + 8 + 9 + 8  | **31** |
| 11. | (2, 4, 1, 3)  | 6 + 6 + 1 + 4  | **17** |
| 12. | (2, 4, 3, 1)  | 6 + 6 + 1 + 8  | **21** |
| 13. | (3, 1, 2, 4)  | 5 + 2 + 3 + 4  | **14** |
| 14. | (3, 1, 4, 2)  | 5 + 2 + 9 + 7  | **23** |
| 15. | (3, 2, 1, 4)  | 5 + 4 + 7 + 4  | **20** |
| 16. | (3, 2, 4, 1)  | 5 + 4 + 9 + 8  | **26** |
| 17. | (3, 4, 1, 2)  | 5 + 6 + 7 + 7  | **25** |
| 18. | (3, 4, 2, 1)  | 5 + 6 + 3 + 8  | **22** |
| 19. | (4, 1, 2, 3)  | 7 + 2 + 3 + 4  | **16** |
| 20. | (4, 1, 3, 2)  | 7 + 2 + 1 + 7  | **17** |
| 21. | (4, 2, 1, 3)  | 7 + 4 + 7 + 4  | **22** |
| 22. | (4, 2, 3, 1)  | 7 + 4 + 1 + 8  | **20** |
| 23. | (4, 3, 1, 2)  | 7 + 8 + 7 + 7  | **29** |
| 24. | (4, 3, 2, 1)  | 7 + 8 + 3 + 8  | **26** |

Dari hasil perhitungan, kombinasi dengan biaya terendah adalah (2,1,3,4) dengan total biaya 13:

(2,1,3,4) -> 6 + 2 + 1 + 4 = 13

### Nomor 2

![Algorithm Diagram](assets/soal-2.png)

jawaban:

```
Algorithm PartitionSubsetSum(arr, n):
    totalSum ← sum(arr)
    
    if totalSum mod 2 ≠ 0 then
        return "Tidak ada solusi"

    target ← totalSum / 2
    subset ← []
    
    if Backtrack(arr, n, 0, 0, target, subset) then
        print "Subset ditemukan:", subset
        print "Sisa elemen:", arr - subset
    else
        print "Tidak ada solusi"

Function Backtrack(arr, n, index, currentSum, target, subset):
    if currentSum = target then
        return True  
    
    if index ≥ n or currentSum > target then
        return False  
    
    subset.append(arr[index])
    if Backtrack(arr, n, index + 1, currentSum + arr[index], target, subset) then
        return True 
    
    subset.pop()
    return Backtrack(arr, n, index + 1, currentSum, target, subset)
```

### Nomor 3

![Algorithm Diagram](assets/soal-3.png)

jawaban:

```
Algorithm GenerateMagicSquare(n):
    numbers ← [1, 2, ..., n^2] 
    all_permutations ← GetAllPermutations(numbers) 

    for each perm in all_permutations do
        matrix ← ConvertToMatrix(perm, n)  
        
        if IsMagicSquare(matrix, n) then
            Print(matrix)   

Function GetAllPermutations(arr):
    if length(arr) == 1 then
        return [arr] 

    result ← [] 
    for each num in arr do
        remaining ← arr - {num} 
        sub_permutations ← GetAllPermutations(remaining)  
        for sub in sub_permutations do
            result.append([num] + sub) 
    return result

Function ConvertToMatrix(perm, n):
    matrix ← []
    for i from 0 to n-1 do
        row ← perm[i*n : (i+1)*n]  
        matrix.append(row)  
    return matrix

Function IsMagicSquare(matrix, n):
    target_sum ← (n * (n^2 + 1)) / 2  

    for i from 0 to n-1 do
        if sum(matrix[i]) ≠ target_sum then
            return False

    for j from 0 to n-1 do
        column_sum ← 0
        for i from 0 to n-1 do
            column_sum += matrix[i][j]
        if column_sum ≠ target_sum then
            return False

    diagonal1_sum ← sum(matrix[i][i] for i from 0 to n-1)
    if diagonal1_sum ≠ target_sum then
        return False

    diagonal2_sum ← sum(matrix[i][n-i-1] for i from 0 to n-1)
    if diagonal2_sum ≠ target_sum then
        return False

    return True  
```