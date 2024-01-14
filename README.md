![logo](resources/icon_256x256.png)

# Helixitty

[Helix](https://helix-editor.com/) + [Alacritty](https://alacritty.org/) = Helixitty, or Alacritty as a UI shell for Helix editor.

This repository contains:

- Git submodules for
  - a [fork](https://github.com/0x6b/alacritty) of Alacritty, based on [v0.13.1](https://github.com/alacritty/alacritty/releases/tag/v0.13.1), with small modifications to make it work as a shell for Helix editor ([diff](https://github.com/alacritty/alacritty/compare/alacritty:alacritty:v0.13.1...0x6b:alacritty:helixitty))
  - a [fork](https://github.com/0x6b/helix) of Helix editor, based on [23.10](https://github.com/helix-editor/helix/releases/tag/23.10), with Japanese specific modifications ([diff](https://github.com/helix-editor/helix/compare/23.10...0x6b:helix:japanese-word-boundary))
- A build script to build both of them, and to create an application bundle for macOS

## Build

```
$ git clone --recursive https://github.com/0x6b/helixitty
$ cargo run -- --release
```

Please note that the `--release` flag is an option for the build script, `src/main.rs`, not for `cargo run`.

## Usage

```console
$ ./target/bin/helixitty [ALACRITTY_OPTIONS] [-- HELIX_OPTIONS] [FILES]
$ # or double-click ./target/app/Helixitty.app
```

For macOS, the build process will create an application bundle `Helixitty.app` in the `target/app` directory, which you can use as a standalone application.

### Limitations

- The application bundle is not signed, so you will need to allow it to run in the security settings.
- Drag and drop won't do what you expect; dragging files from Finder.app to the Helixitty.app will pass the file names to the editor, but the editor will not open them.
- No additional menu items.

## License

Alacritty and Helix are licensed under their own licenses. Other files are licensed under MIT. See [LICENSE](LICENSE).
