# Data Structures and Algorithm Analysis in Java
---  
   
## 七大查找算法   
   
### 1. 顺序查找   
   
![](https://i.imgur.com/urPYd9u.jpg)   
   
   
### 2. 二分查找    
   
![](https://i.imgur.com/V6xCNO1.jpg)   
   
	/** 
	 * 使用递归的二分查找 
	 *title:recursionBinarySearch 
	 *@param arr 有序数组 
	 *@param key 待查找关键字 
	 *@return 找到的位置 
	 */  
	public static int recursionBinarySearch(int[] arr,int key,int low,int high){  
	      
	    if(key < arr[low] || key > arr[high] || low > high){  
	        return -1;                
	    }  
	      
	    int middle = (low + high) / 2;          //初始中间位置  
	    if(arr[middle] > key){  
	        //比关键字大则关键字在左区域  
	        return recursionBinarySearch(arr, key, low, middle - 1);  
	    }else if(arr[middle] < key){  
	        //比关键字小则关键字在右区域  
	        return recursionBinarySearch(arr, key, middle + 1, high);  
	    }else {  
	        return middle;  
	    }     
	      
	}     
   
	/** 
	 * 不使用递归的二分查找 
	 *title:commonBinarySearch 
	 *@param arr 
	 *@param key 
	 *@return 关键字位置 
	 */  
	public static int commonBinarySearch(int[] arr,int key){  
	    int low = 0;  
	    int high = arr.length - 1;  
	    int middle = 0;         //定义middle  
	      
	    if(key < arr[low] || key > arr[high] || low > high){  
	        return -1;                
	    }  
	      
	    while(low <= high){  
	        middle = (low + high) / 2;  
	        if(arr[middle] > key){  
	            //比关键字大则关键字在左区域  
	            high = middle - 1;  
	        }else if(arr[middle] < key){  
	            //比关键字小则关键字在右区域  
	            low = middle + 1;  
	        }else{  
	            return middle;  
	        }  
	    }  
	      
	    return -1;      //最后仍然没有找到，则返回-1  
	}      
    
### 3. 插值查找   
   
![](https://i.imgur.com/QJRCxHF.jpg)    
   
	//插值查找
	int InsertionSearch(int a[], int value, int low, int high)
	{
	    int mid = low+(value-a[low])/(a[high]-a[low])*(high-low);
	    if(a[mid]==value)
	        return mid;
	    if(a[mid]>value)
	        return InsertionSearch(a, value, low, mid-1);
	    if(a[mid]<value)
	        return InsertionSearch(a, value, mid+1, high);
	}   
   
### 4. 斐波那契查找   
   
![](https://i.imgur.com/olafZ2A.jpg)   
   
### 5. 树表查找   
   
![](https://i.imgur.com/QS0McMM.jpg)     
   
[http://www.cnblogs.com/yangecnu/p/Introduce-Binary-Search-Tree.html](http://www.cnblogs.com/yangecnu/p/Introduce-Binary-Search-Tree.html "浅谈算法和数据结构: 七 二叉查找树")    
    
![](https://i.imgur.com/Wpph71O.jpg)    
   
![](https://i.imgur.com/GWrjiBN.jpg)   
    
![](https://i.imgur.com/mlH1Eb0.jpg)   
   
![](https://i.imgur.com/JnJSySi.jpg)    
    
![](https://i.imgur.com/vau1IjH.jpg)    
    
![](https://i.imgur.com/hRDfNab.jpg)    
    
![](https://i.imgur.com/xkiWmg1.jpg)   
   
![](https://i.imgur.com/YFQPuNK.jpg)    
   
![](https://i.imgur.com/1ZLhU2r.gif)   
   
![](https://i.imgur.com/Q8yv82Y.jpg)    
    
[http://blog.codinglabs.org/articles/theory-of-mysql-index.html](http://blog.codinglabs.org/articles/theory-of-mysql-index.html "MySQL索引背后的数据结构及算法原理")     
   
![](https://i.imgur.com/tu9hzQf.jpg)     
    
### 6. 哈希查找    
    
[http://www.cnblogs.com/yangecnu/p/Introduce-Hashtable.html](http://www.cnblogs.com/yangecnu/p/Introduce-Hashtable.html "浅谈算法和数据结构: 十一 哈希表")     
    
