---
title: "Combination of the list"
tags: [recursion]
---

## Combination of the number

```java
public static List<List<Integer>> powerSet(List<Integer> list) {

        List<List<Integer>> lists = new ArrayList<>();

        if(list == null || list.isEmpty())
            return lists;

        helper(list, lists, new ArrayList<Integer>(), 0);

        return lists;
    }

    public static void helper(List<Integer> list, List<List<Integer>> lists, ArrayList<Integer> tmp, int start) {

        lists.add(new ArrayList<Integer>(tmp));

        if(start == list.size()-1)
            return;

        for(int i = start; i < list.size(); i++) {

            //Choose
            tmp.add(list.get(i));

            //explore
            helper(list, lists, tmp, start+1);

            //UnChoose
            tmp.remove(tmp.size()-1);

        }

    }
```