# 如何使用此程式

- 開發軟體環境
- 主程式位置

## 開發軟體環境

![image](https://i.imgur.com/5MPeamM.png)

  要先在電腦上安裝 Java SDK 和 Eclipse IDE 兩套軟體。之後使用 Eclipse IDE 整合開發環境在上面建立 Java 專案，撰寫 Java 程式碼，將 Java 檔編譯成 class 檔，後直接將運行過程和結果輸出在資訊視窗中。

### 下載與安裝
#### 安裝 Java SDK

![image](https://i.imgur.com/FwQDKpO.jpg)
  - 可以 Goolge 搜尋 「Java SE Development Kit 8」，即可以找到目前官方最新版本。
  - 官方連結：https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

#### 安裝 Eclipse IDE
  - 連結：https://www.eclipse.org/
  
## 主程式位置

  - BF法

  // 取得使用者輸入的整數
  
		 		Scanner scanner=new Scanner(System.in);
		 		// 輸入此次作業指定Rod Length值				
		 		System.out.print("Rod length: ");				
		 		int n=scanner.nextInt();				
		 		// 輸出Maximum revenue				
		 		System.out.println("Maximum revenue: "+BruteForceRodcutting(Price,n));
				
  // 雙層循環建立r和s存入切割數點，以及Maximum revenue
  
	static int[] s=new int[100];	
	static int BruteForceRodcutting(int price[],int n)	
	// Bruteforce 暴力法: 列出每種切割方案，比較出Maximum revenue	
	// 所需時間T=O(2^n)	
	{	
		if(n==0)		
			{
				// 無法切割: return 0				
				return 0;			
			} 			
		else		
		{		
			int  q=Integer.MIN_VALUE;  // q無窮小
			for(int i=1;i<=n;i++)			
			{		
				// 取q以及已分割求得的價值中取最大值				
				q=Math.max(q, price[i-1] + BruteForceRodcutting(price, n - i));				
			}			
			return q;			
		}
		
	}
	
   ##### 以上為主要程式內容

  - BD法

  // 取得使用者輸入的整數
    
		 		Scanner scanner=new Scanner(System.in);
		 		// 輸入此次作業指定Rod Length值
		 		System.out.print("Rod length: ");
		 		int n=scanner.nextInt();
		 		// 輸出Maximum revenue
		 		System.out.println("Maximum revenue: "+BottomUpRodcutting(Price,n));
		 		printCuts(Price,n);
    
  // 雙層循環建立r和s存入切割數點，以及Maximum revenue
  
	static int[] s=new int[100];
	static int BottomUpRodcutting(int p[] ,int n) {
	// Bottom-up BD法: 從小排到大來解
	// 所需時間T=O(n^2)
		 int[] r=new int[n+1];
		 r[0]=0;
		 s[0]=0;
		 
	    for(int i = 1; i <= n; i++) {
	        int q =Integer.MIN_VALUE;
	        for(int j = 1; j <= i; j++) {
		        	if(q<p[j] + r[i - j])  // q為Rod Length的最大值
		        	{
		        		q=p[j] + r[i - j];
		        		s[i] = j;  // s記錄取得最大Rod Price的切割點
		        	}
	            }
	        r[i] = q;  // 將最大值存入r[i]中
	        }
	    return r[n];
	}
	 
	static void printCuts(int p[],int n) {
		// 輸出Cuts
		System.out.print("Cuts:");
		while(n > 0) {
			System.out.print(s[n]+" ");
			// 找出對應n的切割點
			n=n-s[n];
		}
		System.out.println();
	}
   ##### 以上為主要程式內容

## 參考資料


- 【從零開始學 Java 程式設計】安裝 JAVA 開發軟體
  - http://tw-hkt.blogspot.com/2019/03/java.html
  
- dp入門——由分桿問題認識動態規劃
  - https://www.cnblogs.com/mozi-song/p/9615167.html

- Dynamic Programming
  - https://jerrywang304.github.io/2017/09/18/Dynamic-Programming/
  
- Dynamic Programming - Rod Cutting
  - https://www.radford.edu/~nokie/classes/360/dp-rod-cutting.html
