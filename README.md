# il2cpp-sys-rs

[![Crates.io](https://img.shields.io/crates/v/il2cpp-sys)](https://crates.io/crates/il2cpp-sys)
[![Docs.rs](https://docs.rs/il2cpp-sys/badge.svg)](https://docs.rs/il2cpp-sys)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

Rust bindings for Unity's Il2Cpp runtime.

## Usage

Add to your `Cargo.toml` dependencies:

```toml
il2cpp-sys-rs = "0.1"
```

### Environment Variables

Configure at build time:

- `UNITY_VERSION`: **Required** - Unity version to target (e.g. "6000.0.47f1")
- `UNITY_DLL_NAME`: **Optional** - Override default "GameAssembly" dll name. Do not suffix with "
  .dll" !

## Supported Versions

Check the [include](include) folder for a list of supported versions.

Generate versions using [Il2CppVersions](https://github.com/nneonneo/Il2CppVersions).

Visit [Unity's editor archive](https://unity.com/releases/editor/archive) for an extensive list of
Unity versions.

## Platform Support

| Platform | Status         | Notes                          |
|----------|----------------|--------------------------------|
| Windows  | ✅ Supported    | Uses `raw-dylib` linking       |
| Linux    | ❌️ Unsupported | No use case for me, PR welcome |
| macOS    | ❌️ Unsupported | No use case for me, PR welcome |
| Android  | ❌️ Unsupported | No use case for me, PR welcome |

## Building

The bindings are automatically generated at compile time. You'll need:

- Rust toolchain
- `bindgen` requirements (clang)

### Custom Unity Versions

1. Add header files to `include/headers/{VERSION}.h`
2. Add API definitions to `include/api/{VERSION}.h`
3. Set `UNITY_VERSION` environment variable during build

## Example

```rust
use il2cpp_sys_rs::il2cpp_domain_get;

fn main() {
    unsafe {
        // Initialize Il2Cpp domain
        let domain = il2cpp_domain_get();
    }
}
```

## Limitations

- **Platform Support**: Currently only supports Windows targets via `raw-dylib` linking
- **Compatibility**: Some applications modify/obfuscate Il2Cpp exports, which may prevent these
  bindings from working

## License

MIT - See [LICENSE](LICENSE) for details.

## Credits

- [Il2CppVersions](https://github.com/nneonneo/Il2CppVersions)
