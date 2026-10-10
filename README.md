# TEK decompression library for Rust

This library is a Rust port of [tek.c](tek.c).

* Pure Rust implementation.
* Supports `no_std` (requires `alloc` and a global allocator for decompression).
* Supports TEK1 (`0x83`), TEK2 (`0x85`), and TEK5 (`0x89`).

## Usage

`tek_getsize` reads the decompressed size from the TEK header.
`tek_decomp` decompresses the input into a `Vec<u8>`.
Both functions return a `Result` with `TekError` on failure.

```rust
use tek::{tek_decomp, tek_getsize, TekError};

fn decompress(input: &[u8]) -> Result<(), TekError> {
    let size = tek_getsize(input)?;
    let output = tek_decomp(input)?;
    assert_eq!(output.len(), size);
    Ok(())
}
```

## License

[KL-01](LICENSE.txt)
