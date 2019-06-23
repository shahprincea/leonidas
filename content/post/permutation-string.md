---
title: "Permutation of the string"
tags: [recursion, string]
---

## Permutation of the String

<p>Given a string return all its permutation. One way to understand this is to draw a tree for small string.</p> 

<p>The high level logic is to print all the permutation with first character lock. Then go into recursion and lock second position and print all its permutation and so on.</p>

<p>Base case is when start point reaches the length of the input string.</p>


```
public List<String> permutation(String str) {
	List<String> list = new ArrayList<>();
	if(str == null || str.isEmpty())
		return list;
	helper(str.toCharArray(), list, 0);
	return list;
}


public void helper(char[] arr, List<String> list, int start) {
	//Base case
	if(start == arr.length-1) {
		list.add(new String(arr));
		return;
	}

	for(int i = 0; i < arr.length; i++) {
		swap(arr, i, start);
		helper(arr, list, start+1);
		swap(arr, i, start);
	}
}


public void swap(char[] arr, int i, int j) {
	char tmp = arr[i];
	arr[i] = arr[j];
	arr[j] = tmp;
}
```