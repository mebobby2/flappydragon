# Flappy Dragon
## Run
```
cargo run
```

## Rust Notes
### String conversion
* To convert a &str to a String in Rust, you can use the to_string() method:
* To convert a String to a &str, you can use the as_str() method
  * Alternatively, you can use the & operator to get a reference to the String as a &str:

### Semicolons
https://stackoverflow.com/questions/26665471/are-semicolons-optional-in-rust

Almost everything in Rust is an expression. An expression is something that returns a value. If you put a semicolon you are suppressing the result of this expression, which in most cases is what you want.

On the other hand, this means that if you end your function with an expression without a semicolon, the result of this last expression will be returned. The same can be applied for a block in a match statement.

```
let a = {
    let inner = 2;
    inner * inner
};
```

Here the expression inner * inner does not end with a semicolon, so its value is not suppressed. Since it is the last expression in the block, its value will be returned and assigned to a. If you put a semicolon on this same line, the value of inner * inner won't be returned.

### ? Operator
https://stackoverflow.com/questions/42917566/what-is-this-question-mark-operator-about

```
fn halves_if_even(i: i32) -> Result<i32, Error> {
    if i % 2 == 0 {
        Ok(i / 2)
    } else {
        Err(/* something */)
    }
}

fn do_the_thing(i: i32) -> Result<i32, Error> {
    let i = match halves_if_even(i) {
        Ok(i) => i,
        Err(e) => return Err(e),
    };

    // use `i`
}
```

Too verbose. Shortened using:
```
fn do_the_thing(i: i32) -> Result<i32, Error> {
    let i = halves_if_even(i)?;

    // use `i`
```

What ? does here is equivalent to the match statement above with an addition. In short:
* It unpacks the Result if OK
* It returns the error if not, calling From::from on the error value to potentially convert it to another type.

## Self
* Title case Self refers to the struct type itself.
* Lowercase self refers to the instance of the structure.

## Book source code

https://github.com/thebracket/HandsOnRust

## Upto
Page 84

Part II

Before that, fix up the game to your liking :)
