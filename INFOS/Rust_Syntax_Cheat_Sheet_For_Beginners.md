Rust match cheat-sheet, designed for clarity, speed, and sanity.


---

#  Rust Syntax Cheat Sheet for Beginners  
### With Explanations & Examples

---

##  Variable Declaration

| Syntax      | Meaning                          | Example |
|-------------|----------------------------------|---------|
| `let`       | Immutable variable               | `let x = 5;` |
| `mut`       | Mutable variable                 | `let mut y = 10; y += 1;` |
| `:`         | Type annotation                  | `let name: String = String::from("Seeu");` |

---

##  Modules & Paths

| Syntax      | Meaning                          | Example |
|-------------|----------------------------------|---------|
| `::`        | Path separator                   | `std::io::stdin();` |
| `use`       | Import module/item               | `use std::collections::HashMap;` |

---

##  Functions & Traits

| Syntax      | Meaning                          | Example |
|-------------|----------------------------------|---------|
| `fn`        | Function declaration             | `fn greet() { println!("Hi!"); }` |
| `impl`      | Implement methods for a type     | `impl Person { fn speak(&self) {} }` |
| `trait`     | Define shared behavior           | `trait Speak { fn talk(&self); }` |

---

##  Macros

| Syntax      | Meaning                          | Example |
|-------------|----------------------------------|---------|
| `!`         | Macro invocation                 | `println!("Hello, world!");` |

---

##  References & Borrowing

| Syntax      | Meaning                          | Example |
|-------------|----------------------------------|---------|
| `&`         | Borrow immutable reference       | `fn greet(name: &str) {}` |
| `&mut`      | Borrow mutable reference         | `fn update(val: &mut i32) { *val += 1; }` |
| `*`         | Dereference pointer              | `let x = 5; let y = &x; println!("{}", *y);` |

---

##  Error Handling

| Syntax      | Meaning                          | Example |
|-------------|----------------------------------|---------|
| `?`         | Propagate error                  | `fn read_file() -> Result<String, io::Error> { let content = fs::read_to_string("file.txt")?; Ok(content) }` |

---

##  Pattern Matching

| Syntax      | Meaning                          | Example |
|-------------|----------------------------------|---------|
| `match`     | Match control flow               | `match number { 1 => "One", _ => "Other" }` |
| `=>`        | Match arm separator              | `match x { true => "Yes", false => "No" }` |

---

##  Type System & Generics

| Syntax      | Meaning                          | Example |
|-------------|----------------------------------|---------|
| `<T>`       | Generic type                     | `fn print<T: Display>(item: T) { println!("{}", item); }` |

---

##  String Handling

```rust
fn main() {
    let name = String::from("Seeu");
    println!("Hello, {}!", name);
}
```

- `String::from()` creates a heap-allocated string.
- `println!` is a macro.
- `{}` is a placeholder for formatting.

---

##  Tips for Remembering Syntax

- **Group symbols by purpose**: macros, borrowing, error handling, etc.
- **Write mini programs** using just one or two concepts.
- **Use comments** in your code to explain each symbol to yourself.
- **Practice with Rustlings** or [Rust by Example](https://doc.rust-lang.org/rust-by-example/) to reinforce patterns.

