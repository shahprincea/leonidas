---
title: "Permutation of the List"
tags: [recursion]
---

## Permutation of the List

<p>Given list of numbers return all its permutation. One way to understand this is to draw a tree for small list.</p> 

<p>The high level logic is to print all the permutation with first number lock. Then go into recursion and lock second position and print all its permutation and so on.</p>

<p>Base case is when start point reaches the size().</p>


```java
public List<List<Integer>> permutation(List<Integer> list) {
	List<List<Integer>> lists = new ArrayList<>();

	//Error Handling
	if(list == null || list.size() == 0)
		return lists;

	helper(list, lists, new ArrayList<Integer>(), 0);

	return lists;
}

public void helper(List<Integer> list, List<List<Integer>> lists, ArrayList<Integer> tmp, int start) {

	if(tmp.size() == list.size()) {
            lists.add(new ArrayList<>(tmp));
            return;
        }

        HashSet<Integer> set = new HashSet<>();
        for(int i = 0; i < list.size(); i++) {

            if(set.contains(list.get(i)))
                continue;
			
			//Choose
            tmp.add(list.get(i));
            set.add(list.get(i));

            //Explore
            helper(list, lists, tmp, start+1);

            //Unchoose
            tmp.remove(tmp.size()-1);
            set.remove(list.get(i));
            
        }
}
```