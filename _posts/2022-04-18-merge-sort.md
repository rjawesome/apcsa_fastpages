

---
toc: true
layout: post
description: Merge Sort Hacks
categories: [cb]
title: Merge Sort
---
# Hack 1/2 (works with any comparable type)
```java
class MergeSort<T extends Comparable<T>> {
    public void sort(List<T> arr, int l, int r)
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

    private void merge(List<T> arr, int l, int m, int r)
    {
        // Find the sizes of two subarrays to be merged
        int n1 = m - l + 1;
        int n2 = r - m;

        /* Create temp arrays */
        List<T> L = new ArrayList<T>(n1);
        List<T> R = new ArrayList<T>(n2);

        /* Copy data to temp arrays */
        for (int i = 0; i < n1; ++i)
            L.set(i, arr.get(l + i));
        for (int j = 0; j < n2; ++j)
            R.set(j, arr.get(m + 1 + j));

        /* Merge the temp arrays */

        // Initial indexes of first and second subarrays
        int i = 0, j = 0;

        // Initial index of merged subarray array
        int k = l;
        while (i < n1 && j < n2) {
            if (L.get(i).compareTo(R.get(j)) <= 0) {
                arr.set(k, L.get(i));
                i++;
            }
            else {
                arr.set(k, R.get(i));
                j++;
            }
            k++;
        }

        /* Copy remaining elements of L[] if any */
        while (i < n1) {
            arr.set(k, L.get(i));
            i++;
            k++;
        }

        /* Copy remaining elements of R[] if any */
        while (j < n2) {
            arr.set(k, R.get(j));
            j++;
            k++;
        }
    }
}
```