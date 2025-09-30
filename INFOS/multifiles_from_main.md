### Step-by-step guide to organizing and running multiple `.rs` files from  `main.rs` in a Rust project.

---

### 🦀 Using Multiple `.rs` Files in Rust   

### 📁 1. Project Structure
Assuming you already have a `main.rs` inside `src/`, here's how your folder might look:

```
src/
├── main.rs
├── foo.rs
├── bar.rs
```

You can also organize files into submodules:

```
src/
├── main.rs
├── utils/
│   ├── mod.rs
│   ├── math.rs
│   └── io.rs
```

---

### 📌 2. Declare Modules in `main.rs`

To use `foo.rs` and `bar.rs`, declare them as modules:

```rust
mod foo;
mod bar;

fn main() {
    foo::say_hello();
    bar::add(2, 3);
}
```

---

### 🧩 3. Define Functions in Each File

#### `foo.rs`
```rust
pub fn say_hello() {
    println!("Hello from foo!");
}
```

#### `bar.rs`
```rust
pub fn add(a: i32, b: i32) -> i32 {
    println!("Sum is: {}", a + b);
    a + b
}
```

---

### 📦 4. If Using Subfolders (e.g. `utils`)

#### In `main.rs`:
```rust
mod utils; // This loads utils/mod.rs

fn main() {
    utils::math::double(4);
    utils::io::print_message();
}
```

#### In `utils/mod.rs`:
```rust
pub mod math;
pub mod io;
```

#### In `utils/math.rs`:
```rust
pub fn double(x: i32) -> i32 {
    println!("Double is: {}", x * 2);
    x * 2
}
```

#### In `utils/io.rs`:
```rust
pub fn print_message() {
    println!("Message from utils::io");
}
```

---

### 🚀 5. Run Your Project

Just run:

```bash
cargo run
```

Rust will compile all the modules and execute `main.rs`.
