---
title: Rust Lifetimes
date: "2020-06-15T09:00:00.0Z"
layout: post
draft: false
path: "/posts/rust-lifetimes"
category: "web development"
tags:
  - "rust"
  - "lifetimes"
  - "ownership"
description: "Some simple examples of Rust lifetime parameters usage."
---

So, you've decided to deep dive into Rust lifetime parameters. Nice!  

Let's talk about when dinosaurs roamed the earth.  

### SIMPLE CASE, COMPILER APPROVED ✅

[this simple snippet in a Rust sandbox][rust-sandbox:simple]

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
struct Dinosaur {
  location: Earth,
    period: Period,
    name: String,
}

fn main() {
  let montana = Earth {
    location: String::from("Montana"),
    };

    let jurassic = Period {
      age: String::from("Jurassic"),
    };

    let t_rex = Dinosaur {
      name: String::from("Tyrannosaurus Rex"),
        location: montana,
        period: jurassic,
    };

    println!("{:?}", t_rex.name);
    println!("{:?}", t_rex.location);
    println!("{:?}", t_rex.period);
    
    // compiler disallows these next lines, why?
    // println!("{:?}", montana); 
    // println!("{:?}", jurassic); 
}
```

Our aim here is to create a Rust compiler-approved Dinosaur struct, incorporating `Earth` and `Period` structs. This is what we have after a first pass of putting some props into a few `struct` objects.  

At the bottom of the snippet is a commented-out line that the compiler does not allow. Why? Because `montana` and `jurassic` are now owned by `t_rex` and access to their values is now only allowed via `t_rex`. This is not how we want the code to behave.

Some more change is left to be done with the code, but this is the basic idea. We want a dinosaur to have knowledge of its location and its time period... but definitely not for the `struct` itself to own the `Earth` and `Period` structs.

### SLIGHTLY LESS NAÏVE APPROACH, NOT COMPILER-FRIENDLY YET ❌

Now let's say you decide to start experimenting with Rust references and come up with this idea:

```rust
struct Dinosaur {
    location: &Earth,
    period: &Period,
    name: String,
}
```

### LIFETIME PARAMETER INFORMED CASE, COMPILER APPROVED ✅

But even before running any business logic between the structs, the compiler already wants to know more, it wants explicit lifetime parameters on `Dinosaur`, so you dig around and put this together:

[this lifetime snippet in a Rust sandbox][rust-sandbox:with-lifetime-a]

```rust
#[derive(Debug)]
struct Earth {
    location: String,
}

#[derive(Debug)]
struct Period {
    age: String,
}

// instead of receiving the values `location` and `period`,
// Dinosaur borrows (pre-existing) instances of Earth, Period
#[derive(Debug)]
struct Dinosaur<'a> {
    location: &'a Earth,
    period: &'a Period,
    name: String,
}

fn main() {
    let montana = Earth {
        location: String::from("Montana"),
    };

    let jurassic = Period {
       age: String::from("Jurassic"),
    };

    let t_rex = Dinosaur {
        name: String::from("Tyrannosaurus Rex"),
        location: &montana,
        period: &jurassic,
    };

    println!("{:?}", t_rex.name);
    
    println!("ACCESSING MONTANA DIRECTLY {:?}", montana); 
    println!("ACCESSING JURASSIC DIRECTLY {:?}", jurassic); 
}
```

In a nutshell:

- `Dinosaur` is receiving `location` and `period` as borrowed references. 
- Since `Dinosaur` does not own the values, the Rust compiler wants explicit confirmation that the original value that the references refer to will still be valid as long as `Dinosaur` needs them.
- This explicit confirmation comes in the form of lifetime parameters, on `Dinosaur<&'a>`.

### HANDLING SEVERAL LIFETIMES IN A SINGLE STRUCT

_"But why doesn't each prop in `Dinosaur` gets its own letter? What about this `<'a, 'b>` that I saw somewhere on Stack Overflow? How does that work?"_

Oh, you mean something like `Dinosaur<'a, 'b>` , right? So each of the letters represents a different scope that the struct knows about. Here is a [link to the official documentation][rust-book:borrow-checker], but the important part of it right now is the following snippet, illustrating what the lifetime parameters signify in terms of scopes.

```rust
{
    let r;                // ---------+-- 'a
                          //          |
    {                     //          |
        let x = 5;        // -+-- 'b  |
        r = &x;           //  |       |
    }                     // -+       |
                          //          |
    println!("r: {}", r); //          |
}                         // ---------+
```

I'll leave integrating this stuff into our `Dinosaur` example up to you, o dear reader of mine.

[rust-sandbox:simple]: https://play.rust-lang.org/?version=stable&mode=debug&edition=2015&code=%23!%5Ballow(unused)%5D%0A%23%5Bderive(Debug)%5D%0Astruct%20Earth%20%7B%0A%20%20%20%20location%3A%20String%2C%0A%7D%0A%0A%23%5Bderive(Debug)%5D%0Astruct%20Period%20%7B%0A%20%20%20%20age%3A%20String%2C%0A%7D%0A%0A%23%5Bderive(Debug)%5D%0Astruct%20Dinosaur%20%7B%0A%20%20%20%20location%3A%20Earth%2C%0A%20%20%20%20period%3A%20Period%2C%0A%20%20%20%20name%3A%20String%2C%0A%7D%0A%0Afn%20main()%20%7B%0A%20%20%20%20let%20montana%20%3D%20Earth%20%7B%0A%20%20%20%20%20%20%20%20location%3A%20String%3A%3Afrom(%22Montana%22)%2C%0A%20%20%20%20%7D%3B%0A%0A%20%20%20%20let%20jurassic%20%3D%20Period%20%7B%0A%20%20%20%20%20%20%20%20age%3A%20String%3A%3Afrom(%22Jurassic%22)%2C%0A%20%20%20%20%7D%3B%0A%0A%20%20%20%20let%20t_rex%20%3D%20Dinosaur%20%7B%0A%20%20%20%20%20%20%20%20name%3A%20String%3A%3Afrom(%22Tyrannosaurus%20Rex%22)%2C%0A%20%20%20%20%20%20%20%20location%3A%20montana%2C%0A%20%20%20%20%20%20%20%20period%3A%20jurassic%2C%0A%20%20%20%20%7D%3B%0A%0A%20%20%20%20println!(%22%7B%3A%3F%7D%22%2C%20t_rex)%3B%0A%7D%0A

[rust-sandbox:with-lifetime-a]: https://play.rust-lang.org/?version=stable&mode=debug&edition=2015&code=%23%5Bderive(Debug)%5D%0Astruct%20Earth%20%7B%0A%20%20location%3A%20String%2C%0A%7D%0A%0A%23%5Bderive(Debug)%5D%0Astruct%20Period%20%7B%0A%20%20%20%20age%3A%20String%2C%0A%7D%0A%0A%23%5Bderive(Debug)%5D%0A%2F%2F%20instead%20of%20receiving%20the%20values%20%60location%60%20and%20%60period%60%2C%0A%2F%2F%20Dinosaur%20borrows%20(pre-existing)%20instances%20of%20Earth%2C%20Period%0Astruct%20Dinosaur%3C'a%3E%20%7B%0A%20%20%20%20location%3A%20%26'a%20Earth%2C%0A%20%20%20%20period%3A%20%26'a%20Period%2C%0A%20%20%20%20name%3A%20String%2C%0A%7D%0A%0A%0Afn%20main()%20%7B%0A%20%20let%20montana%20%3D%20Earth%20%7B%0A%20%20%20%20location%3A%20String%3A%3Afrom(%22Montana%22)%2C%0A%20%20%20%20%7D%3B%0A%0A%20%20%20%20let%20jurassic%20%3D%20Period%20%7B%0A%20%20%20%20%20%20age%3A%20String%3A%3Afrom(%22Jurassic%22)%2C%0A%20%20%20%20%7D%3B%0A%0A%20%20%20%20let%20t_rex%20%3D%20Dinosaur%20%7B%0A%20%20%20%20%20%20name%3A%20String%3A%3Afrom(%22Tyrannosaurus%20Rex%22)%2C%0A%20%20%20%20%20%20%20%20location%3A%20%26montana%2C%0A%20%20%20%20%20%20%20%20period%3A%20%26jurassic%2C%0A%20%20%20%20%7D%3B%0A%0A%20%20%20%20println!(%22%7B%3A%3F%7D%22%2C%20t_rex.name)%3B%0A%20%20%20%20%0A%20%20%20%20println!(%22ACCESSING%20MONTANA%20DIRECTLY%20%7B%3A%3F%7D%22%2C%20montana)%3B%20%0A%20%20%20%20println!(%22ACCESSING%20JURASSIC%20DIRECTLY%20%7B%3A%3F%7D%22%2C%20jurassic)%3B%20%0A%7D

[rust-book:borrow-checker]: https://doc.rust-lang.org/book/ch10-03-lifetime-syntax.html?highlight=%27b#the-borrow-checker