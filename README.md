## 構造体とは
変数を同時に複数宣言する配列というものがありました。ですが、配列では同じ型の変数しか宣言できません。

そこで、違う型の変数をまとめて宣言したいとき、構造体というものを使います。。例えば、次の変数をまとめて宣言したいとします。
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

例として、先の構造体humanの構造体変数dataを5個宣言し、二番目のage要素にアクセスするプログラムを示します。
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
