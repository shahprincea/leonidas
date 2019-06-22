---
title: "Merge Sort"
tags: [sort]
---

## Sorting

Merge sort is comparison based sorting. 

- <strong>Algo</strong> : Divide and Conquer 
- <strong>Time complexity</strong> : O(nlog(n)) 
- <strong>Space Complexity</strong> : O(n) 


```
public void mergeSort(int[] arr) {

	//Error handling
	if(arr == null || arr.length == 0)
		return;

	int[] aux = new int[arr.length];	
	mergeSort(arr, aux, 0, arr.length-1);	
}


public void mergeSort(int[] arr, int[] aux, int left, int right) {
	if(left < right) {

		int mid = left + (right - left)/2;

		//Divide
		mergeSort(arr, aux, left, mid);
		mergeSort(arr, aux, mid+1, right);
		merge(arr, aux, left, mid, right);
	}
}

//Merge two sorted array
public void merge(int[] arr, int[] aux, int left, int mid, int right) {
	int i = left, j = mid + 1, k = left;

	while(i <= mid && j <= right) {
		if(arr[i] < arr[j]) 
			aux[k] = arr[i++];
		else 
			aux[k] = arr[j++];
		k++;
	}

	while(i <= mid) {
		aux[k++] = arr[i++];
	}

	while(j <= right) {
		aux[k++] = arr[j++];
	}

	for(int p = left; p <= right; p++) {
		arr[p] = aux[p];
	}
}
```