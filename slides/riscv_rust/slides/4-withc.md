# Cから呼び出す
* rustから使いやすいようにCを書く
* rustを書く
* `staticlib`として書き出す
* cbindgenで`.h`ファイルを作る
* 一緒にコンパイルする

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

## staticlib
Cargo.toml
```toml
[package]
name = "blink"
version = "0.1.0"
authors = ["Daniel"]
edition = "2018"

[lib]
crate-type=["staticlib"]

[dependencies]
```

---

## cbindgen

```bash
$ cargo install cbindgen
$ cbindgen .
....
void blink_rs(void);
```

---

## 一緒にコンパイルする
* コンパイラに`staticlib`も投げればコンパイルしてくれる。
* 今回は`Makefile`の依存関係に書くだけでコンパイルしてくれた。


