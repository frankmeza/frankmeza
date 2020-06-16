---
title: Rust Lifetimes
date: "2020-06-15T09:00:00.0Z"
layout: post
draft: true
path: "/posts/rust-lifetimes"
category: "web development"
tags:
  - "rust"
  - "lifetimes"
  - "ownership"
description: "Some simple examples to better understand use of Rust lifetimes."
---

This set of an examples uses these structs:

```rust
#[derive(Debug)]
struct Earth {
    location: String,
}

#[derive(Debug)]
struct Period {
    age: String,
}

#[derive(Debug)]
// instead of receiving the values `location` and `period`,
// Dinosaur borrows (pre-existing) instances of Earth, Period
struct Dinosaur<'a> {
    location: &'a Earth,
    period: &'a Period,
    name: String,
}
```

In a nutshell:

- `Dinosaur` is receiving `location` and `period` as borrowed references. 
- Since `Dinosaur` does not own the values, the Rust compiler wants explicit confirmation that the original value that the references refer to will still be valid as long as `Dinosaur` needs them.
- This explicit confirmation comes in the form of lifetime parameters

```rust
// this does not compile with error: 
// `missing lifetime specifier, expected named lifetime parameterrustc(E0106)`
struct Dinosaur {
    location: &Earth,
    period: &Period,
    name: String,
}
```

### Simple Case, Compiles

```rust
// using structs above

fn main() {
    let montana = Earth {
        location: String::from("Montana"),
    };

    let jurassic = Period {
        age: String::from("Jurassic"),
    };

    let t_rex = Dinosaur {
        name: String::from("Tyrannosaurus Rex"),
        location: &montana, // 'a
        period: &jurassic,   // 'b
    };

    println!("{:?}", t_rex);
}
```

There's no problem with the above, as the references to `montana` and `jurassic` are still valid when `t_rex` needs to use them.

