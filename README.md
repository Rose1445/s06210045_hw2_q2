# 如何使用此程式

- 開發軟體環境
- 主程式位置

## 開發軟體環境

![image](https://i.imgur.com/9DYIRXC.png)

Dev-C++
是一套免費並且開放原始碼的C++程式設計軟體，附上GNU GCC編譯器，體積小功能強大。
它包括多頁面視窗、工程編輯器，在工程編輯器中集合了編輯器、編譯器、連接程式和執行程式；
也提供高亮度語法顯示的，以減少編輯錯誤。

### 下載與安裝
#### 安裝 Dev-C++

![image](https://i.imgur.com/gaa770w.png)
  - 教學連結：http://selfinquiring.hatenablog.com/entry/2016/03/18/204352
  - 官方連結：https://sourceforge.net/projects/orwelldevcpp/
  
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

- 【C++】C++中幾種測試程式執行時間的方法
  - https://www.itread01.com/content/1548646212.html
  
- Dynamic Programming - Rod Cutting
  - https://www.radford.edu/~nokie/classes/360/dp-rod-cutting.html
