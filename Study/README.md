# Objective-C メモ

### 参考書籍＆WEB

##### サルにもできるiPhoneアプリの作り方
http://ameblo.jp/micro-garden/entry-10309905035.html
  
##### 詳細! Objective-C iPhoneアプリ開発 入門ノート Xcode5+iOS7対応
http://www.amazon.co.jp/Objective-C-iPhone%E3%82%A2%E3%83%97%E3%83%AA%E9%96%8B%E7%99%BA-%E5%85%A5%E9%96%80%E3%83%8E%E3%83%BC%E3%83%88-Xcode5-iOS7%E5%AF%BE%E5%BF%9C/dp/4800710227




# @ と ＃
@ ・・・ C言語に対してObjective-Cで拡張されたコードあることを示す  
＃ ・・・ は「プリプロセッサ命令」、プロセスが始まる前に動く命令のこと  




# 演算子 (数値演算子、代入演算子、他)
JSとほぼ一緒。  
ただ、代入する変数に型指定が必要。  
また、=== はない(そもそも型指定があるから？)  




# 変数
JSと違って型指定が必須。  
Xcodeでは、利用していない変数がある場合に、警告が出る。

#### 型
int : 整数(負〜正)  
NSinteger : 整数(負〜正) ビット長が変わる  
unsigned int : 0 と正の整数  
NSUInteger : 0 と正の整数 ビット長が変わる  
double : 小数点がある場合  
float : 小数点がある場合、代入時に末尾にfをつける(例) float gap = 12.345f;  
BOOL : true/false の２択 YES or 1, NO or 0 (jsと同じで true,falseでもOK)
char : 半角英数字を１文字だけ入れることができる


#### キャスト
型変換のこと


#### typtedef 
型指定を任意の文字で設定できる



#### ポインタ型の変数は変数名の前に *を付ける
```
データ型 *変数名;
```

Objective-Cでインスタンス変数を宣言する時に、
型がクラスオブジェクト型の場合は、変数名の頭にアスタリスクを付ける。

- 1. インスタンス変数を宣言している
- 2. そのインスタンスの型は、クラスオブジェクト　




# 定数
const で宣言。
.hファイルや .mのクラス宣言部分で定義する

enum 列挙型の定義,連番が入る
```
enum {
  NUM_A = 10,
  NUM_B,
  NUM_C
};
```


#### define
定数を定義できる(PHPのdefine的な。。。)
```
#define URL @"test.com"
NSLog(@"URLは%@", URL); // URLはtest.com
```

尚、undef で解除可能



#NSLog()

ログを表示できます。 jsのconsole.log();  
ただし、デフォルトでは文字列だけ。  
数値とか、オブジェクトとかのログを出したい場合は、  
フォーマット指定子と呼ばれるものを記載する必要あり。  
```
int a,b;
a = 10;
b = 20;
NSLog(@"はじめに%d、次に%d、最後に%d", b, a,b); //はじめに20、次に10、最後に20  
```
### フォーマット指定子
%d 数値  
%@ オブジェクト  
%s 文字列  




# if
if分はjsと一緒


# switch
jsと似ているけど、値の部分を、定数定義してあげないといけない
```
NSInteger YEAR = 2010;
NSInteger const A=2009;
NSInteger const B=2010;

switch(YEAR){
    case A:
        NSLog(@"A");
        break;
    case B:
        NSLog(@"B");
        break;
    default:
        NSLog(@"Other");
        break;
}
```




# for
jsと代替一緒



# スコープ
jsと違って変数の範囲が{}に閉じ込められる。




# オブジェクトとクラス

オブジェクト：プロパティとメソッドをもったもののこと。  
プロパティ：オブジェクトの属性(色とかテキストとか)  
メソッド：関数やね。  
メンバ：プロパティとメソッドを合わせてメンバと呼ぶ。  
クラス：オブジェクトを作るための仕様書＆設計図。  

#### プロパティ
プロパティはjsとほぼ一緒。.繋ぎ。  
```
_myfield.text = @"test";  
```

#### メソッド

#### メソッドの実行
変な形。しかも複数の引数がある場合の書式がきもい。  

>[オブジェクトさん、 引数を元にメソッドして]  

みたいな感じ。

```
[オブジェクト名 メソッド名:引数];  
[オブジェクト名 メソッド名:引数1 ラベル2:引数2 ラベル3:引数3];
```

引数1のラベルはメソッド名そのものになる。


#### メソッドの定義もまた、気持ち悪い。

クラスメソッドの定義  
\+ (返り値のデータ型) メソッド名
\+ (返り値のデータ型) メソッド名:(引数1のデータ型) 引数1 ラベル2:(引数2のデータ型)引数2....
  
インスタンスメソッドの定義  
\- (返り値のデータ型) メソッド名
\- (返り値のデータ型) メソッド名:(引数1のデータ型) 引数1 ラベル2:(引数2のデータ型)引数2....


## クラスメソッドとインスタンスメソッド
クラスメソッド : クラスに対して実行するメソッド ( リファレンスでは \+ で表記される)  
インスタンスメソッド : インスタンス（クラスから作られたオブジェクト）に対して実行するメソッド ( リファレンスでは - で表記される)  


# インスタンス
クラスから作成されたオブジェクトのこと。  


# スーパークラスとサブクラス
スーパークラス：継承元のクラスのこと  
サブクラス：継承を利用して作られたクラスのこと  


# インスタンスの作成
クラスからインスタンスを作る場合下記が必要  


1. インスタンス作成  
\+ (id)alloc  

2. インスタンス初期化  
\+ (id)init  





# プログラム内の * は何？
Objective-Cでインスタンス変数を宣言する時に、
型がクラスオブジェクト型の場合は、変数名の頭にアスタリスクを付ける。

1. インスタンス変数を宣言している
2. そのインスタンスの型は、クラスオブジェクト　


# アウトレットとアクション

アウトレット：
アクション：

IBOutle は アウトレットである宣言
```
IBOutlet UIWindow *window;
MyViewController *myViewController;
```



#import　関連プログラムの呼び出し

@interface ～ @end　クラスの宣言
@implementation ～ @end　クラスの実装


# アクセサ
- セッターメソッド（インスタンス変数にデータを格納するメソッド）  
- ゲッターメソッド（インスタンス変数からデータを取得するメソッド）  

「インスタンス変数にアクセス（set,get）するもの」のこと  
そのメソッドなので、アクセサメソッドと呼ぶ



# ディレクティブ（命令）

アクセサメソッドを自動生成してくれるもの  
@property（宣言） と @synthesize（実装） でセット  

#### ＜例＞  
```
@property (nonatomic, retain) UIWindow *window;
@property (nonatomic, retain) MyViewController *myViewController;

@synthesize window;
@synthesize myViewController;
```

「【UIWindow型】の【Window】っていうインスタンス変数にアクセスよろしく」
「【myViewController型】の【myViewController】っていうインスタンス変数にアクセスよろしく」


# デリゲート（代理人）
アプリケーションの起動時・終了時に、アプリケーション固有の動作を行う必要がある場合があり、
その際に処理を依頼するオブジェクトのことをデリゲートと呼ぶ。




# 文字列操作
```
// --------------------------------------------------

// 文字列操作

// --------------------------------------------------


// 文字を表示する
NSString *myString = @"こんにちは";
NSString *myString2 = @"赤ちゃん";
NSLog(@"%@%@",myString,myString2);

// 文字列を連結 stringByAppendingString
NSString *Hello = [myString stringByAppendingString:myString2];
NSLog(@"--------------------------------------------");
NSLog(@"%@",Hello);


// 文字列を連結 stringWithFormat
NSString *text1 = @"たなか";
NSString *text2 = @"いちろー";
NSString *text3 = [NSString stringWithFormat:@"%@の%@",text1,text2];
NSLog(@"--------------------------------------------");
NSLog(@"%@",text3);

// 文字列の長さを調べる
NSInteger txt_length = text3.length;
NSLog(@"--------------------------------------------");
NSLog(@"文字数：%d",txt_length);


// 文字列検索 rangeOfString / JS の indexOf的な
// rangeOfString,返値の型はNSRange
// .locationで0から数えて一致した場所
// .locationで一致しない場合は、NSNotFound（）

NSString *keyword = @"なか";
NSRange range = [text3 rangeOfString:keyword];
NSLog(@"--------------------------------------------");
if(range.location == 0){
    NSLog(@"「%@」は含まれていない",keyword);
}else{
    // 「なか」は含まれていますが出力される
    NSLog(@"「%@」は含まれています",keyword);
}


// 文字列の比較
NSString *deffTxt1 = @"iPhone4";
NSString *deffTxt2 = @"iPhone5";

NSLog(@"--------------------------------------------");
// あれ、普通に == で比較できちゃう？
if(deffTxt1 == deffTxt2){
    NSLog(@"deffTxt1 と deffTxt2 は一緒です");
}else{
    NSLog(@"deffTxt1 と deffTxt2 は一緒じゃない");
}

// 文字列は isEqualToString で比較
NSLog(@"--------------------------------------------");
if([deffTxt1 isEqualToString:deffTxt2]){
    NSLog(@"deffTxt1 と deffTxt2 は一緒です");
}else{
    NSLog(@"deffTxt1 と deffTxt2 は一緒じゃない");
}

// 文字列置換 [stringByReplacingOccurrencesOfString:HOGE_BEFORE widthString:HOGE_AFTER]
// jsの  var text_after = text_before.replace('1','2');
NSString *replaceTxt1 = @"iPhone5最高!!!!";
NSString *replaceAfterTxt = [replaceTxt1 stringByReplacingOccurrencesOfString:@"!" withString:@"?"];
NSLog(@"置換後のテキスト：%@",replaceAfterTxt);
```


#配列
```
//配列の作成
NSArray *myArray = @[@"ipad",@"iPhone4",@"iPod"];
NSLog(@"--------------------------------------------");
NSLog(@"myArray = %@",myArray);

int num1 = 100;
float num2 = 0.55;
NSArray *myArray2 = @[@(num1),@(num2)];
NSLog(@"--------------------------------------------");
NSLog(@"myArray2 = %@",myArray2);


// 配列を取り出す
NSLog(@"--------------------------------------------");
NSLog(@"%@",myArray[2]);

// 配列の要素数 count
NSLog(@"--------------------------------------------");
NSLog(@"%d",myArray.count);


NSLog(@"--------------------------------------------");
// 要素の固定が確定していない場合の配列
// NSMutableArray で作った配列では、配列の追加・削除（ミュータブル）が可能

NSMutableArray *iOS = [NSMutableArray array];
[iOS addObject:@"iPad"];
[iOS addObject:@"iPhone"];
// 配列にまとめてオブジェクトを挿入
[iOS addObjectsFromArray:@[@"iPhone4",@"iPhone5",@"iPhone6"]];
// 配列に配列を挿入
[iOS addObject:@[@"iPhone7",@"iPhone8",@"iPhone9"]];
NSLog(@"iOS = %@",iOS);
NSLog(@"--------------------------------------------");
NSLog(@"iOS = %@",iOS[5][1]);


// --------------------------------------------------

// 辞書（Dictionary） = jsでいうオブジェクト{key1:value1,key2:value2}

// --------------------------------------------------
NSLog(@"--------------------------------------------");
NSDictionary *Soccer = @{
    @"香川":@"マンU",
    @"岡崎":@"マインツ",
    @"本田":@"ミラン"
};
NSLog(@"%@",Soccer[@"香川"]);


NSLog(@"--------------------------------------------");
// 要素の追加、削除が可能（ミュータブル）な辞書。
NSMutableDictionary *Football = [NSMutableDictionary dictionaryWithCapacity:3];
// 辞書を追加
Football[@"遠藤"] = @"G大阪";
Football[@"長友"] = @"インテル";
NSLog(@"%@",Football[@"長友"]);

// --------------------------------------------------

// 構造体

// --------------------------------------------------
typedef struct _box{
    uint width;
    uint height;
    char type;
} Box;

Box box1,box2;

box1.width = 150;
box1.height = 200;
box1.type = "AAA";
```


# ヘッダファイル(.h)、実装ファイル(.m)

下記は、ほかのどのテンプレートでも必ず作成される基本ファイル。　
こいつをベースにして、アプリを構築する。  
AppDelegate .h .m ・・・ アプリ起動時・復帰時・終了時のもろもろの処理  
ViewController .h .m ・・・画面の操作時の処理  
  
# インターフェースセクション / クラスエクステンション
.m（実装ファイル） 内の インナーフェースセクションは、  
宣言したクラス内のみにスコープがしぼられ、  
別途クラスエクステンションとも呼ばれる。  
  
.h（宣言ファイル） 内にもインターフェスセクションがあるが、  
こちらは、クラスエクステンションとは呼ばないのかも。  

クラスを宣言する。
```
@interface ViewController ()
@end
```

# インプリメンテーションセクション

インターフェースセクションで宣言したプロパティを初期化したり  
メソッドとかを定義したりするブロック。

```
@implementation ViewController
@end
```

# インスタンス自身のメソッドとプロパティへのアクセス

自分のプロパティにアクセスする際（jsでいうところの this かな）は、
```
self.プロパティ
```
でアクセス。

```
_プロパティ
```

でもアクセス可能。

# スコープ
グローバルで使いたい変数は、  
.h　で宣言するか
@interface ~@end で宣言しておく。

基本的な流れとして、
1. クラスエクステンションで変数やメソッドの宣言をする
2. ほかのクラスからアクセスしたくなったら、ヘッダファイルに移す。


# Xcodeで複数行インデント
複数行選択して、Tabボタンを押すと消える。。。
下記でインデント可能。
```
Command + ]
Command + [
```

# プロジェクト作成時に自動的に用意されるメソッド
```
// [デフォルト処理] アプリ起動後、画面が表示される前に自動的に呼び出されるメソッド
- (void)viewDidLoad{
}
```

```
// [デフォルト処理]アプリのメモリ使用量が大幅に増加した際に、自動的に呼び出されるメソッド
- (void)didReceiveMemoryWarning{
    [super didReceiveMemoryWarning];
    // Dispose of any resources that can be recreated.
}
```


# Objective-CのnilとNULLの違い
nilはnullオブジェクトを表し、オブジェクトが未初期化であることや、  
クリアされた状態であることを表わすのに使用される。


# アプリ起動後に何かしたい時のタイミング

iOS7だとviewDidLoadのタイミングで  
Viewの操作をしようとすると動かないとか。

```
- (void)viewDidLoad
{
    // Viewが表示される最初の1回だけ呼ばれる
    NSLog(@"viewDidLoad");
}
- (void)viewWillAppear:(BOOL)animated
{
    // Viewが表示される直前に呼ばれる
    NSLog(@"viewWillAppear");
}
- (void)viewDidAppear:(BOOL)animated
{
    // Viewの表示完了後に呼ばれる
    NSLog(@"viewDidAppear");
}
- (void)viewWillDisappear:(BOOL)animated
{
    // Viewが別のViewへ切り替わる直前に呼ばれる
    NSLog(@"viewWillDisappear");
}
- (void)viewDidDisappear:(BOOL)animated
{
    // Viewが別のViewへ切り替わった後に呼ばれる
    NSLog(@"viewDidDisappear");
}
```
