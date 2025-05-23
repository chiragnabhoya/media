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

### Media Methods
```rust
impl Media {
    fn description(&self) -> String {
        match self {
            Media::Book { title, author } => format!("Book: {} {}", title, author),
            Media::Movie { title, director } => format!("Movie: {} {}", title, director),
            Media::Audiobook { title } => format!("Audiobook: {}", title),
            Media::Podcast(id) => format!("Podcast: {}", id),
            Media::Placeholder => String::from("Placeholder"),
        }
    }
}
```
The `description` method provides formatted output for each media type.

### Catalog Struct
```rust
#[derive(Debug)]
struct Catalog {
    items: Vec<Media>,
}
```
The `Catalog` struct manages a collection of `Media` items.

### Catalog Methods
```rust
impl Catalog {
    fn new() -> Self {
        Catalog { items: vec![] }
    }

    fn add(&mut self, media: Media) {
        self.items.push(media);
    }

    fn get_by_index(&self, index: usize) -> Option<&Media> {
        if self.items.len() > index {
            Some(&self.items[index])
        } else {
            None
        }
    }
}
```
The `Catalog` provides methods to create a new catalog, add items, and retrieve items by index safely.

## Example Usage
```rust
fn main() {
    let audiobook = Media::Audiobook { title: String::from("An Audiobook") };
    let good_movie = Media::Movie { title: String::from("Good Movie"), director: String::from("Good Director") };
    let bad_book = Media::Book { title: String::from("Bad Book"), author: String::from("Bad Author") };
    let podcast = Media::Podcast(10);
    let placeholder = Media::Placeholder;

    let mut catalog = Catalog::new();
    catalog.add(audiobook);
    catalog.add(good_movie);
    catalog.add(bad_book);
    catalog.add(podcast);
    catalog.add(placeholder);

    match catalog.get_by_index(9990) {
        Some(value) => println!("Item: {:#?}", value),
        None => println!("No value here!"),
    }
}
```
This example demonstrates how to create a catalog, add media items, and retrieve them safely.

## Installation & Running
1. Ensure you have Rust installed: [Rust Installation Guide](https://www.rust-lang.org/tools/install)
2. Clone this repository:
   ```sh
   git clone https://github.com/your-repo/media-catalog.git
   cd media-catalog
   ```
3. Run the project:
   ```sh
   cargo run
   ```

## License
This project is licensed under the MIT License.
