---
toc: true
layout: post
description: Binary Search Hacks
categories: [cb]
title: Binary Search
---

## Hack 1/2
```java

public class BinarySearch {
    public static void sort(int arr[], int l, int r)
    {
        if (l < r) {
            // find midpoint
            int m = l + (r - l) / 2;
    
            // sort top and bottom half
            sort(arr, l, m);
            sort(arr, m + 1, r);
    
            // merge the two sub arrays
            merge(arr, l, m, r);
        }
    }
    
    public static void merge(int arr[], int l, int m, int r)
    {
        // Find the sizes of two subarrays to be merged
        int n1 = m - l + 1;
        int n2 = r - m;

        /* Create temp arrays */
        int[] L = new int[n1];
        int[] R = new int[n2];

        /* Copy data to temp arrays */
        for (int i = 0; i < n1; ++i)
            L[i] = arr[l + i];
        for (int j = 0; j < n2; ++j)
            R[j] = arr[m + 1 + j];

        /* Merge the temp arrays */

        // Initial indexes of first and second subarrays
        int i = 0, j = 0;

        // Initial index of merged subarray array
        int k = l;
        while (i < n1 && j < n2) {
            if (L[i] <= R[j]) {
                arr[k] = L[i];
                i++;
            }
            else {
                arr[k] = R[i];
                j++;
            }
            k++;
        }

        /* Copy remaining elements of L[] if any */
        while (i < n1) {
            arr[k] = L[i];
            i++;
            k++;
        }

        /* Copy remaining elements of R[] if any */
        while (j < n2) {
            arr[k] = R[j];
            j++;
            k++;
        }
    }

    public static int binarySearch(int e, int[] arr, int l, int r) {
        if (l == r) return arr[l] == e ? l : -1;
        int m = (l + r)/2;
        if (e <= arr[m]) {
            return binarySearch(e, arr, l, m);
        }
        return binarySearch(e, arr, m+1, r);
    }
    
    public static void main (String[] args) {
        int array[] = {1, 3, 5, 7, 9, 23, 45, 67};
        sort(array, 0, array.length - 1);
        System.out.println(binarySearch(45, array, 0, array.length - 1));
    }
}
```