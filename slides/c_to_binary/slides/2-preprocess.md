# プリプロセス

コンパイル前に必要な前処理をするステップ
```
gcc main.c -E -o main.i
```

---

```c
#define HELLO "Hello World!\n"

int main() {
    print(HELLO);
    return 0;
}
```
↓
```c
int main() {
    print("Hello World!\n");
    return 0;
}
```

---

```c
#include<stdio.h>
int main() {...}
```
↓
```c
//
// 圧倒的分量のstdio.h
//
// ここらへんにprintf()とか定義されてる
//

int main() {...}
```