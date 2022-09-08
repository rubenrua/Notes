Print memory
```
let size = 10;
let view = v_ptr as *const i32;
for i in 0..size {
    print!("{:02x} ", unsafe {*view.offset(i)});
}
```