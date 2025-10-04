##  What Is `match`?

`match` is Rust’s powerful control flow tool—like a turbo-charged `switch` statement from other languages, but safer and more expressive.

```rust
match value {
    pattern1 => action1,
    pattern2 => action2,
    _ => default_action,
}
```

---

##  Basic Usage

```rust
let number = 5;

match number {
    1 => println!("One"),
    2 | 3 => println!("Two or Three"), // multiple patterns
    4..=6 => println!("Between 4 and 6"), // range
    _ => println!("Something else"), // wildcard
}
```

---

##  Matching Enums

```rust
enum Direction {
    North,
    South,
    East,
    West,
}

let dir = Direction::North;

match dir {
    Direction::North => println!("Up"),
    Direction::South => println!("Down"),
    _ => println!("Sideways"),
}
```

---

##  Matching with `Option<T>`

```rust
let maybe_name = Some("Seeu");

match maybe_name {
    Some(name) => println!("Hello, {}", name),
    None => println!("No name found"),
}
```

---

##  Matching with `Result<T, E>`

```rust
let result: Result<i32, &str> = Ok(42);

match result {
    Ok(val) => println!("Success: {}", val),
    Err(e) => println!("Error: {}", e),
}
```

---

##  Destructuring Tuples

```rust
let pair = (3, "Rust");

match pair {
    (0, _) => println!("Zero and anything"),
    (x, y) => println!("{} and {}", x, y),
}
```

---

## Guards (Extra Conditions)

```rust
let x = 5;

match x {
    n if n % 2 == 0 => println!("Even"),
    n if n % 2 != 0 => println!("Odd"),
    _ => println!("Who knows"),
}
```

---

##  Binding with `@`

```rust
let age = 15;

match age {
    teen @ 13..=19 => println!("Teenager: {}", teen),
    _ => println!("Not a teen"),
}
```

---

##  Nested Matching

```rust
enum Status {
    Active,
    Inactive,
}

enum User {
    Admin(Status),
    Guest,
}

let user = User::Admin(Status::Active);

match user {
    User::Admin(Status::Active) => println!("Admin is active"),
    User::Admin(Status::Inactive) => println!("Admin is inactive"),
    User::Guest => println!("Guest user"),
}
```

---

##  `match` Returns Values

```rust
let score = 85;

let grade = match score {
    90..=100 => "A",
    80..=89 => "B",
    70..=79 => "C",
    _ => "F",
};

println!("Grade: {}", grade);
```

---

##  Tips

- Every possible case must be handled—Rust won’t compile otherwise.
- Use `_` as a catch-all for unmatched patterns.
- `match` is an **expression**, so it can return values.
- Prefer `match` over `if let` when handling multiple patterns.

