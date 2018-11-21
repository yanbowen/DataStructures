# Data Structures and Algorithm Analysis in Java
---  
  
### 选择，冒泡，直接插入排序   
   
排序是数据处理中十分常见且核心的操作，虽说实际项目开发中很小几率会需要我们手动实现，毕竟每种语言的类库中都有n多种关于排序算法的实现。但是了解这些精妙的思想对我们还是大有裨益的。本文简单温习下最基础的三类算法：选择，冒泡，插入。    
   
先定义个交换数组元素的函数，供排序时调用   
   
	   /**
	     * 交换数组元素
	     * @param arr
	     * @param a
	     * @param b
	     */
	    public static void swap(int []arr,int a,int b){
	        arr[a] = arr[a]+arr[b];
	        arr[b] = arr[a]-arr[b];
	        arr[a] = arr[a]-arr[b];
	    }    
    
#### 简单选择排序    
   
简单选择排序是最简单直观的一种算法，基本思想为**每一趟从待排序的数据元素中选择最小（或最大）的一个元素作为首元素**，直到所有元素排完为止，简单选择排序是**不稳定排序**。    
    
	public static viod selectSort(int[] arr){
	
		for(int m=0; m<arr.length-1; m++){
			for(int n=m+1; n<arr.length;n++){
				if(arr[m]>arr[n]){
					int temp = arr[m];
					arr[m] = arr[n];
					arr[n] = temp;
				}
			}
		}
	}    
   
#### 冒泡排序   

冒泡排序的基本思想是，对相邻的元素进行两两比较，顺序相反则进行交换，这样，每一趟会将最小或最大的元素“浮”到顶端，最终达到完全有序。   
   
	public static viod bubbleSort(int[] arr){
	
		for(int m=0; m<arr.length-1; m++){
			for(int n=0; n<arr.length-m-1;n++){
				if(arr[n]>arr[n+1]){
					int temp = arr[n];
					arr[n] = arr[n+1];
					arr[n+1 ] = temp;
				}
			}
		}
	}   
    
#### 直接插入排序   
   
直接插入排序基本思想是**每一步将一个待排序的记录，插入到前面已经排好序的有序序列中去，直到插完所有元素为止。**   
   
    public static void insertionSort(int[] arr) {
        for (int i = 1; i < arr.length; i++) {
            int j = i;
            while (j > 0 && arr[j] < arr[j - 1]) {
                swap(arr,j,j-1);
                j--;
            }
        }
    }    
    
![](https://i.imgur.com/Ycqun2g.jpg)    
     
### 希尔排序   
   
![](https://i.imgur.com/Lxu49hK.jpg)   
   
![](https://i.imgur.com/tU6A8Tx.jpg)   
   
![](https://i.imgur.com/DZmYkpV.jpg)   
    
![](https://i.imgur.com/L21YwjY.jpg)   
   
### 归并排序    
   
![](https://i.imgur.com/2djeNLN.jpg)    
     
![](https://i.imgur.com/PwYTgw4.jpg)   
   
![](https://i.imgur.com/M10rZ6x.jpg)

![](https://i.imgur.com/hM3X6N3.jpg)   
    
    
### 快速排序——三数取中法   
   
[https://blog.csdn.net/morewindows/article/details/6684558](https://blog.csdn.net/morewindows/article/details/6684558)    
   
快速排序由C. A. R. Hoare在1962年提出。它的基本思想是：通过一趟排序将要排序的数据分割成独立的两部分，其中一部分的所有数据都比另外一部分的所有数据都要小，然后再按此方法对这两部分数据分别进行快速排序，整个排序过程可以递归进行，以此达到整个数据变成有序序列   
   
![](https://i.imgur.com/KHPbk9m.jpg)   
   
![](https://i.imgur.com/DBKzaGD.jpg)    
   
![](https://i.imgur.com/JEm3ALF.jpg)   
   
![](https://i.imgur.com/EukIJcu.jpg)   
   
