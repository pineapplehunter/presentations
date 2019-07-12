# アセンブル

---

```c
int main () {
    printf ("Hello World!");
    return 0;
}
```

↓

```asm
...
    .globl  main    
    .type   main, @function    
main:    
.LFB0:    
    .cfi_startproc    
    pushq   %rbp    
    .cfi_def_cfa_offset 16    
    .cfi_offset 6, -16    
    movq    %rsp, %rbp    
...
```

