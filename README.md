# 如何使用此程式

- 開發軟體環境
- 主程式位置

## 開發軟體環境

![image](https://i.imgur.com/9DYIRXC.png)

Dev-C++是一套免費並且開放原始碼的C++程式設計軟體，附上GNU GCC編譯器，體積小功能強大。
它包括多頁面視窗、工程編輯器，在工程編輯器中集合了編輯器、編譯器、連接程式和執行程式；
也提供高亮度語法顯示的，以減少編輯錯誤。

### 下載與安裝
#### 安裝 Dev-C++

![image](https://i.imgur.com/gaa770w.png)
  - 教學連結：http://selfinquiring.hatenablog.com/entry/2016/03/18/204352
  - 官方連結：https://sourceforge.net/projects/orwelldevcpp/
  
## 主程式位置

  	char X[512];
  	char Y[512]; 
  	int  i,j,m,n;
  	int len=0;
	time_t 	time1, time2;	   
	FILE 	*fp;
	char  cell;
  	
  	// 初始化 X, Y 字串  
  	// 將內存中的內容全部設置為指定的值，做初始化工作。
	memset(X, 0x0, sizeof(512));
  	memset(Y, 0x0, sizeof(512));   
  	
  	// 讀取輸入檔
	// 使用者輸入0讀取 hw2_lcs1.txt， 輸入1則讀取 hw2_lcs2.txt
    printf("輸入0 讀取 hw2_lcs1.txt， 輸入1 讀取 hw2_lcs2.txt:  ");
    scanf("%d", &i); 
    
    if(i==0) 
    {
    	// 開啟檔案，將檔案內容以字元讀入的方式，顯示在電腦螢幕上。
    	fp = fopen("hw2_lcs1.txt", "r");
	} 
	else 
	{
		fp = fopen("hw2_lcs2.txt", "r");
	}
	
	// 讀入 X,Y字串 
	while (!feof(fp))
	{
		fscanf(fp, "%c\n", &cell);
		if(cell == 'x') 
		{
			fscanf(fp, "%s\n", X);	
		} 
		else 
		{ 
			fscanf(fp, "%s\n", Y);	
		}
	}
	// 印出 X,Y 字串 
	printf("X=\n%s\n\n", X);
	printf("Y=\n%s\n\n", Y);
	
	// 取得字串長度  
    m = strlen(X);
	n = strlen(Y);
	
	// 利用LCS長度找出LCS 
  	len = LCS( X, Y, m, n );
  	printf("LCS 長度 : %d\n", len ); 
  	printf("LCS = ");
  	print_lcs(X, m, n);
  	printf("\n");
	
   ##### 以上為主要程式內容

## 參考資料


- C++變數型態
  - https://www.csie.ntu.edu.tw/~b98902112/cpp_and_algo/cpp/variable_type_and_declare.html

- 【C++】C++中幾種測試程式執行時間的方法
  - https://www.itread01.com/content/1548646212.html
  
- 演算法筆記－Longest Common Subsequence
  - http://www.csie.ntnu.edu.tw/~u91029/LongestCommonSubsequence.html
