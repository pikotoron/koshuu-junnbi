## switch文
以前条件分岐として、if文というのをやりました。もう一つ、switch文という条件分岐があるので説明します。

switch文は、簡単に言えば番号分けで判断する条件分岐です。if文の場合、
```
if (i < 10) {
  処理；
}
```
のように整数の値の範囲などで判断したりしますが、switch文は定数で判断します。

switch文は次のように書きます。
```
switch (条件式) {
  case 数値:
    実行文;
    break;
    
  case 数値:
    実行文;
    break;
}
```

例として、
```
通学生の番号:1
寮生の番号　:2
```
とし、数値を入力して番号で通生か寮生か判断するプログラムを示します。
```
#include <stdio.h>

int main(void)
{
  int no;
  scanf("%d",&no);

  switch (no) {
  case 1:
    printf("あなたは通生ですね。\n");
    break;

  case 2:
    printf("あなたは寮生ですね。\n");
    break;

  default: //1,2以外が入力されたとき実行
    printf("あなたは教員だったんですか。\n");
    break;
  }

  return 0;
}
```
switch文を書く時、break文を忘れてしまうとcaseがつながってしまうので注意してください。


## 構造体とは
変数を同時に複数宣言する配列というものがありました。ですが、配列では同じ型の変数しか宣言できません。

そこで、違う型の変数をまとめて宣言したいとき、構造体というものを使います。例えば、次の変数をまとめて宣言したいとします。
```
char name[40]; //名前の文字列を格納する配列
int age; //年齢
double height; //身長
double weight; //体重
```

構造体は次のように宣言します。
```
struct 構造体タグ名 { 
  宣言したい要素; //構造体内で宣言した要素のことをメンバという
};
```
このとき構造体タグ名が、構造体そのものの名前になります。今回はhumanという名前を付けます。

構造体にまとめると、次のようになります。
```
struct human {
  char name[40];
  int age;
  double height;
  double weight;
};
```

そして、次のように構造体変数を宣言します。
```
struct 構造体タグ名 構造体変数名;
```
実際に構造体を使うために、構造体変数を宣言する必要があります。

例として、構造体と構造体変数を宣言するプログラムを示します。
```
#include <stdio.h>

struct human {
  char name[40];
  int age;
  double height;
  double weight;
};

int main(void)
{
  struct human data; //human型の構造体変数dataを宣言

  return 0;
}
```

配列では各要素を番号によって扱っていましたが、構造体では要素名を扱います。要素を扱うとき、
```
構造体変数名.要素名
```
のようにします。

次のプログラムは先の構造体のage要素にアクセスする例です。
```
#include <stdio.h>

struct human {
  char name[40];
  int age;
  double height;
  double weight;
};

int main(void)
{
  struct human data;

  data.age = 18;
  printf("%d\n",data.age);

  return 0;
}
```

```
18 //実行結果
```

また、次のように構造体を宣言することができます。typedefを使うことで、呼び出すときのstructを省略できます。
```
typedef struct {
  char name[40];
  int age;
  double height;
  double weight;
} human;
```

この後、構造体変数を宣言することは変わりませんが、少し書き方が変わります。
```
#include <stdio.h>

typedef struct {
  char name[40];
  int age;
  double height;
  double weight;
} human;

int main(void)
{
  human data; //structを書かない

  data.age = 18;
  printf("%d\n",data.age);

  return 0;
}
```

一般的にはこちらの書き方を使います。


## 構造体の配列
構造体変数は構造体そのものが変数として扱われます。すなわち、構造体を配列のようにいくつも宣言することができるのです。

構造体の配列は次のように宣言します。
```
構造体タグ名 構造体変数名[要素数];
```

例として、先の構造体humanの構造体変数dataを5個宣言し、3番目のage要素にアクセスするプログラムを示します。
```
#include <stdio.h>

typedef struct {
  char name[40];
  int age;
  double height;
  double weight;
} human;

int main(void)
{
  human data[5];

  data[2].age = 18;
  printf("%d\n",data[2].age);

  return 0;
}
```

同様に、要素の番号を変えることで任意の番号の構造体の要素にアクセスすることができます。

例えば、5番目の構造体のname要素とheight要素にアクセスして入力したいとき、
```
#include <stdio.h>

typedef struct {
  char name[40];
  int age;
  double height;
  double weight;
} human;

int main(void)
{
  human data[5];

  scanf("%s",data[4].name);
  scanf("%lf",&data[4].height);

  printf("data[4].name = %s\n",data[4].name);
  printf("data[4].height = %.1fcm\n",data[4].height);

  return 0;
}
```
と書くことができます。


## 構造体の引数
構造体変数も一つの変数なので、関数の引数にし、一度に複数の情報を渡すことができます。例として、human_print関数に引数として構造体を渡すプログラムを示します。
```
#include <stdio.h>

typedef struct {
  char name[40];
  int age;
  double height;
  double weight;
} human;

void human_print(human);

int main(void)
{
  human data;

  scanf("%s",data.name);
  scanf("%d",&data.age);
  scanf("%lf",&data.height);
  scanf("%lf",&data.weight);

  human_print(data);

  return 0;
}

void human_print(human data)
{
  printf("%s\n",data.name);
  printf("%d歳\n",data.age);
  printf("%.1fcm\n",data.height);
  printf("%.1fkg\n",data.weight);
}
```
