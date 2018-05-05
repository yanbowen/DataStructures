# Data Structures and Algorithm Analysis in Java
---  
   
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