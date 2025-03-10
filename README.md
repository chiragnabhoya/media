# Media Catalog

A simple Rust project that demonstrates the use of enums, structs, and methods to create a media catalog system.

## Features
- Define different types of media: Books, Movies, Audiobooks, Podcasts, and Placeholders.
- Implement an enum `Media` to represent various media types.
- Provide a `description` method to get a formatted string description of each media type.
- Maintain a collection of `Media` items using a `Catalog` struct.
- Add media items dynamically to the catalog.
- Retrieve media items by index safely.

## Technologies Used
- Rust

## Code Overview
### Media Enum
```rust
#[derive(Debug)]
enum Media {
    Book {title: String, author: String},
    Movie {title: String, director: String},
    Audiobook {title: String},
    Podcast (u32),
    Placeholder,
}
```
This enum represents different types of media that can be stored in the catalog.
