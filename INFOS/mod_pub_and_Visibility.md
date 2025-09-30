Break down Rust’s module system and visibility rules to structure Rust project and control access across files.

---

##  Core Concepts: `mod`, `pub`, and Visibility

### 🔹 `mod`: Declaring a Module
- Tells Rust to include another file or submodule.
- Can be declared in `main.rs`, `lib.rs`, or any other `.rs` file.

```rust
mod foo; // Looks for foo.rs or foo/mod.rs
```

### 🔹 `pub`: Making Things Public
- By default, everything in a module is private.
- Use `pub` to expose functions, structs, enums, etc. to other modules.

```rust
// foo.rs
pub fn greet() {
    println!("Hello from foo!");
}
```

Without `pub`, `foo::greet()` would be inaccessible from `main.rs`.

---

##  Visibility Rules

| Item         | Default Visibility | Use `pub` to Access From |
|--------------|--------------------|---------------------------|
| Functions    | Private             | Other modules             |
| Structs      | Private             | Other modules             |
| Struct fields| Private             | Other modules             |
| Enums        | Private             | Other modules             |
| Enum variants| Public (if enum is `pub`) | Other modules     |

###  Example: Struct with Private Field

```rust
pub struct User {
    pub name: String,
    age: u32, // private
}

impl User {
    pub fn new(name: String, age: u32) -> Self {
        Self { name, age }
    }

    pub fn age(&self) -> u32 {
        self.age
    }
}
```

You can access `user.name`, but not `user.age` directly—only via the method.

---

##  Nested Modules

### Structure:
```
src/
├── main.rs
├── network/
│   ├── mod.rs
│   └── http.rs
```

### `main.rs`
```rust
mod network;

fn main() {
    network::http::connect();
}
```

### `network/mod.rs`
```rust
pub mod http;
```

### `network/http.rs`
```rust
pub fn connect() {
    println!("Connecting via HTTP...");
}
```

---

##  Common Pitfalls

-  Forgetting `pub` on both the module and the item.
-  Trying to access private fields directly.
-  Misplacing `mod` declarations (must match file structure).
