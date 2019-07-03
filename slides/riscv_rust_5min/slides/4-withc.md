# Cから呼び出す
* rustから使いやすいようにCを書く
* rustを書く

---

## rustから使いやすいようにCを書く
* freedom-e-sdk
```c
void led_on() {...}

void led_off() {...}

int main() {
    ...

    blink_rs();
}
```

---

## rustを書く
```rust
extern {
    fn led_on();
    fn led_off();
}

#[no_mangle]
pub extern fn blink_rs() {
    loop {
        unsafe{ led_on(); }
        delay();

        unsafe{ led_off(); }
        delay();
    }
}
```

---

* panicについて書く
* `staticlib`として書き出す
* cbindgenで`.h`ファイルを作る
* 一緒にコンパイルする

---

# これで動きます！