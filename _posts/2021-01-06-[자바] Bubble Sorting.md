---
title: "[자바] 실습과제 - Bubble Sorting"
categories:
    - dev
tags:
    - dev
    - java 
toc: true

---

# Bubble Sorting

```Java
package sorting;

public class BubbleSort implements Sortable {

	@Override
	public void ascending(int[] arr) {
		// TODO Auto-generated method stub
		System.out.println("BubbleSort ascending 결과>>>");
		int count = 0;
		int temp = 0;
		
		while( count<arr.length ) {
			++count;
			for(int i =0;i<arr.length - count;i++) {
				if(arr[i]>arr[i+1]) {
					temp = arr[i];
					arr[i] = arr[i + 1];
					arr[i + 1] = temp;
				}
			}
		}
		// ascending 결과 출력
		for (int i=0; i < 30; i++) { 
			System.out.printf("%3d ",arr[i]);
		}
		System.out.println();
		System.out.println();
	}

	@Override
	public void descending(int[] arr) {
		// TODO Auto-generated method stub
		System.out.println("BubbleSort descending 결과>>>");
		int count = 0;
		int temp = 0;
		
		while( count<arr.length ) {
			++count;
			for(int i =0;i<arr.length - count;i++) {
				if(arr[i]<arr[i+1]) {
					temp = arr[i];
					arr[i] = arr[i + 1];
					arr[i + 1] = temp;
				}
			}
		}
		// descending 결과 출력
		for (int i=0; i < 30; i++) { 
			System.out.printf("%3d ",arr[i]);
		}
		System.out.println();
		System.out.println();
	}

	@Override
	public void description() {
		// TODO Auto-generated method stub
		Sortable.super.description();
		System.out.println("BubbleSort 입니다.");		
	}
}

```


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTMxMzAxNjg0MywtMjA1OTYxNTAxN119
-->