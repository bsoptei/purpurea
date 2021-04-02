# purpurea
This crate provides attribute based convenience method generation (accessor/updater/mutator/constructor) for structs with private fields.
The observed results achieved by the crate's attibute macros are somewhat similar to that of the `@Getter`/`@Setter` and the `@RequiredArgsConstructor`/`@AllArgsConstructor` annotations of __Java__ library [Lombok](https://projectlombok.org/), with a __Rust__ flavor.

# Example
```
mod examples {
    use purpurea::*;
    
    #[accessors(email)]
    #[updaters(email)]
    #[default_constructor]
    pub struct User {
        email: String,
        account_number: usize
    }
}
     
use examples::*;

let john_doe = User::new("john_doe@example.com", 45275);
let new_email = "john_doe@example2.com";
let john_doe2 = john_doe.with_email(new_email.to_owned());

assert_eq!(new_email, john_doe2.email());
 ```
