## `ms2-rs` ⏱️
> ms2 is a Rust library that recreates the ms package from TypeScript for Rust. It helps you convert milliseconds to human-readable time strings and vice versa. If you need to work with time in your Rust project, ms2 makes it easy.

### Features:
- ⏳ Convert time strings (like "2 days") to milliseconds.
- ⏱️ Convert milliseconds to time strings.
- ⏲️ Supports common time units like seconds, minutes, hours, and days.
- 👍 Easy-to-use API based on the ms package from TypeScript.
- 🍒 Possibility to import `format` or `parse` to use explicit and typesafe methods

### Usage:
Add ms2 to your Cargo.toml:

```toml
[dependencies]
ms2 = "0.2.0"
```

Then use it in your code:

```rust
use ms2::ms;

fn main() {
    let ms_output = ms("2 days").unwrap();
    match ms_output {
        ms2::MsOutput::Milliseconds(ms) => println!("{}", ms), // Outputs: 172800000
        _ => panic!("Expected milliseconds"),
    }
}
```

#### Using `ms2` with an integer input to convert to a human-readable string

```rust
use ms2::ms;

fn main() {
    let time_str_output = ms(172800000).unwrap();
    match time_str_output {
        ms2::MsOutput::Str(time_str) => println!("{}", time_str), // Outputs: "2 days"
        _ => panic!("Expected string"),
    }
}
```

#### Using the convenience methods `unwrap_number` and `unwrap_str`

```rust
use ms2::{ms, UnwrapMsOutput};

fn main() {
    let ms_value = ms("1 hour").unwrap_number();
    println!("{}", ms_value); // Outputs: 3600000

    let time_str = ms(3600000).unwrap_str();
    println!("{}", time_str); // Outputs: "1 hour"    
}

```

#### Use raw explicit and typesafe methods `format` and `parse`
```rust
use ms2::{format, parse};

fn main() {
    println!("parse(\"60 seconds\") = {}", parse("60 seconds").unwrap()); // parse("60 seconds") = 60000
    println!("format(172_800_000) = {}", format(172_800_000)); // format(172_800_000) = 2 days
}
```

#### Support for negative values
```rust
use ms2::{format, parse};

fn main() {
    println!("parse(\"-60 seconds\") = {}", parse("-60 seconds").unwrap()); // parse("-60 seconds") = -60000
    println!("format(-172_800_000) = {}", format(-172_800_000)); // format(-172_800_000) = -2 days
}
```

### Contributing:
Contributions are welcome! Check the `CONTRIBUTING.md` file for more info.

### License:
This project is licensed under the MIT License. See the LICENSE file for details.
