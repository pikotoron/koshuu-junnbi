## メモリと変数
パソコンやスマートフォンにはメモリ(RAM)という記憶装置があります。このメモリには1、または0の状態を記憶しておく部品が大量に入っていて、例えるならば、超巨大な一列ロッカーのような構造をしています。
ロッカー一個一個を1ビットと数え、これらを8個ワンセットで1バイトとし、メモリ内では1バイトごとに番号が割り振られています。
変数を宣言すると、メモリ上に一つの塊としてその変数の領域が確保されます。確保される領域の広さは、変数の型によって異なり、int型なら4バイト、double型なら8バイトです。
変数はメモリ上に存在するため、確保された場所の番号によって区別されます。区別する番号のことをアドレスといいます。

例として、アドレスを参照するプログラムを示します。
```
#include <stdio.h>

int main(void)
{
  int i; 
  printf("%p\n",&i); //%pでアドレスを表示

  return 0;
}
```

実行した結果は次のようになりました。
```
./a.out 
0x7fff702e52fc //変数iのアドレスの値
```
ただし、実行結果は環境によって異なります。


## ポインタとは
アドレスを参照してメモリ上の変数に直接アクセスするためのものとして、ポインタ変数があります。ポインタ変数は次のように宣言します。
```
int *p; //あくまでポインタ変数はp。int*型の変数pと考えてください。
```

またポインタ変数を複数宣言するとき、
```
int *p1,p2,p3;
```
と宣言すると、p1,p2は普通のint型の変数になってしまうので、
```
int *p1,*p2,*p3;
```
のように宣言します。
