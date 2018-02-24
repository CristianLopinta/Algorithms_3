1. Problema
Encontrar la cantidad de inversiones en una matriz (Usando Merge Sort)

La cantidad de inversiones de una matriz indica: qué tan lejos (o cerca) está la matriz de ser ordenada. Si el conjunto ya está ordenado, el recuento de inversión es 0. Si el conjunto se ordena en orden inverso, el recuento de inversión es el máximo.

De manera más clara, dos elementos a [i] y a [j] forman una inversión si a [i]> a [j] e i <j

https://ideone.com/muQGln

    def merge(arr, l, m, r):
        n1 = m - l + 1
        n2 =  r - m 
        L = [None]*n1
        R = [None]*n2
        for i in range(n1):
            L[i] = arr[l + i]
        for j in range(n2):
            R[j] = arr[m + 1+ j]
    ##    i = 0
    ##    j = 0
    ##    k = l
        c = 0
        for i in range(n1):
            for j in range(n2):
                if (L[i] > R[j]):
                    c+=1
    ##            k+=1
    ##    while (i < n1):
    ##        arr[k] = L[i]
    ##        i+=1
    ##        k+=1
    ##    while (j < n2):
    ##        arr[k] = R[j]
    ##        j+=1
    ##        k+=1
        return c
    def mergeSort(arr, l, r):
        if (l < r):
            m = l+(r-l)//2
            c1 = mergeSort(arr, l, m)
            c2 = mergeSort(arr, m+1, r)
            c3 = merge(arr, l, m, r)
            return c1+c2+c3
        else:
            return 0
    a = [1, 20, 6, 4, 5]
    c = mergeSort(a,0,len(a)-1);
    print("#Inversiones =",c)
