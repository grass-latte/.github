# Grass Latte

A graphical web logger enabling easier debugging - particularly with multiple threads.

## Key Features

- A hierarchical, collapsable widget tree
- No references to widgets maintained - code doesn't need to be modified to pass widget references around
```rust
grass_latte::send_text(["Buttons", "Incrementer", "Value"], format!("{val}"), false);
```
- Multithreading support
- Pollable buttons (no references needed)
```rust
while !grass_latte::poll_button(["Start"], "Start", false) {
    thread::sleep(Duration::from_millis(200));
}
```
- Buttons with callbacks
```rust
grass_latte::send_button_with_callback(
    ["Buttons", "Incrementer"],
    "Click button to increment".to_string(),
    false,
    callback.clone(),
);
```
- Support for multiple projects (including different languages) to connect to the same Grass Latte web interface
- Each Grass Latte library has the web interface bundled
```rust
grass_latte::serve_webpage();
```

## Repositories

- [`grass-latte-web`](https://github.com/grass-latte/grass-latte-web) - Code to generate the one-file web interface used by and bundled with all Grass Latte libraries
- [`grass-latte-rs`](https://github.com/grass-latte/grass-latte-rs) - Rust library for Grass Latte
    - [`grass-latte-example-rs`](https://github.com/grass-latte/grass-latte-example-rs) - Example usage of [`grass-latte-rs`](https://github.com/grass-latte/grass-latte-rs)
- [`grass-latte-py`](https://github.com/grass-latte/grass-latte-py) - Python proof-of-concept library for Grass Latte
- [`grass-latte-server-rs`](https://github.com/grass-latte/grass-latte-server-rs) - A standalone CLI for serving the Grass Latte web interface, for when you want multiple projects to connect to the same interface but don't want to pick a specific project to serve it

## Screenshot

![Grass Latte Interface](/profile/grass_latte.png)