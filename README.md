# fslint-plugin-sdk

SDK with helper utilities for [FSLint](https://github.com/hyperpolymath/file-soup) plugin development.

## Overview

This crate provides helper utilities for building plugins for FSLint. It re-exports `fslint-plugin-api` and adds useful helpers for:

- Path manipulation
- File metadata
- Common file patterns
- Context helpers

## Usage

Add to your `Cargo.toml`:

```toml
[dependencies]
fslint-plugin-sdk = "0.1"
```

## Modules

### `path` - Path helpers

```rust
use fslint_plugin_sdk::path;

let ext = path::extension(Path::new("file.txt"));  // Some("txt")
let hidden = path::is_hidden(Path::new(".hidden")); // true
```

### `metadata` - File metadata helpers

```rust
use fslint_plugin_sdk::metadata;

let age = metadata::age_in_days(modified_time);
let size = metadata::format_size(1024 * 1024);  // "1.00 MB"
```

### `patterns` - Common file patterns

```rust
use fslint_plugin_sdk::patterns::{Patterns, matches};

if matches(path, &Patterns::node_modules()) {
    // Skip node_modules
}

if matches(path, &Patterns::image_files()) {
    // Handle images
}
```

### `context` - Plugin context helpers

```rust
use fslint_plugin_sdk::context;

let rel_path = context::relative_path(&ctx);
let size = context::file_size(&ctx);
```

## License

MIT OR Apache-2.0
