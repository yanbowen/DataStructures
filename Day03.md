# Data Structures and Algorithm Analysis in Java
---  
  
## 冒泡排序  
   
	public static void bubbleSort3(int [] a, int n){
    	int j , k;
    	int flag = n ;//flag来记录最后交换的位置，也就是排序的尾边界

    	while (flag > 0){//排序未结束标志
    	    k = flag; //k 来记录遍历的尾边界
    	    flag = 0;

    	    for(j=1; j<k; j++){
    	        if(a[j-1] > a[j]){//前面的数字大于后面的数字就交换
    	            //交换a[j-1]和a[j]
    	            int temp;
    	            temp = a[j-1];
    	            a[j-1] = a[j];
    	            a[j]=temp;

    	            //表示交换过数据;
    	            flag = j;//记录最新的尾边界.
    	        }
    	    }
    	}
	}    
   
	/**
	 * 冒泡排序的第一种实现, 没有任何优化
	 * @param a
	 * @param n
	 */
	public static void bubbleSort1(int [] a, int n){
    	int i, j;

    	for(i=0; i<n; i++){//表示n次排序过程。
    	    for(j=1; j<n-i; j++){
    	        if(a[j-1] > a[j]){//前面的数字大于后面的数字就交换
    	            //交换a[j-1]和a[j]
    	            int temp;
    	            temp = a[j-1];
    	            a[j-1] = a[j];
    	            a[j]=temp;
    	        }
    	    }
    	}
	}// end   
   
![](https://i.imgur.com/3gUNcZR.jpg)   
   
   
	/*
	题目描述
		现在雷雷知道哪些麦田之间可以建设水渠和建设每个水渠所需要的费用（注意不是所有麦田之间都可以建立水渠）。
		请问灌溉所有麦田最少需要多少费用来修建水渠。
	输入
		4 4
		1 2 1
		2 3 4
		2 4 2
		3 4 3
	输出
		6
	*/
	import java.util.PriorityQueue;
	import java.util.Queue;
	import java.util.Scanner;
	
	public class A16_ZuiXiaoShengChengShu {
		// 最小生成树
		private static int f[] = new int[1005];
		public static class Edges implements Comparable<Edges> {
			public int a, b, c;
	
			public int compareTo(Edges arg0) {
				return this.c - arg0.c;
			}
		}

		static int find(int a) {
			if (f[a] != a) {
				f[a] = find(f[a]);
			}
			return f[a];
		}

		public static void main(String[] args) {
			int index = 0;
			Queue<Edges> queue = new PriorityQueue<Edges>(1000);
			Scanner scanner = new Scanner(System.in);

			int n = scanner.nextInt();
			int m = scanner.nextInt();
			Edges[] rets = new Edges[m];

			for (int i = 0; i <= n; i++) {
				f[i] = i;
			}
			Edges edge = null;
			for (int i = 1; i < m + 1; i++) {
				edge = new Edges();
				edge.a = scanner.nextInt();
				edge.b = scanner.nextInt();
				edge.c = scanner.nextInt();
				queue.add(edge);
		}
		scanner.close();

		int sum = 0;
		int i = 1;
		n--;
		while (n > 0 && i <= m) {

			// 返回第一个元素并删除
			Edges abc = queue.poll();
			int a = find(abc.a);
			int b = find(abc.b);
			// 如果a!=b意味着“边i”与“已经添加到最小生成树中的顶点”没有环路径
			if (a != b) {
				f[a] = b;
				sum += abc.c;
				n--;
				rets[index++] = abc;
			}
			i++;
		}
		System.out.println(sum);

		for (int icount = 0; icount < index; icount++)
			System.out.println(rets[icount].a + " - " + rets[icount].b);
	}
	}