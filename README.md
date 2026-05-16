# homeos-plugin-homebrew-tap

![License](https://img.shields.io/badge/license-MIT%20OR%20Apache--2.0-blue)

A [homeos](https://github.com/hainet50b/homeos) plugin that adds a [Homebrew tap](https://docs.brew.sh/Taps) on macOS or Linux. Use it as a dependency of packages installed via the [homebrew plugin](https://github.com/hainet50b/homeos-plugin-homebrew) when those packages live in a third-party tap.

## Usage

Add the plugin to your homeos repository:

```sh
homeos plugin add homebrew-tap
```

Define a setup package that adds the tap, and have the actual package depend on it:

```sh
$ homeos package add homebrew-tap-hashicorp --plugin homebrew-tap --param name=hashicorp/tap
$ homeos package add terraform --plugin homebrew --param name=hashicorp/tap/terraform --depends-on homebrew-tap-hashicorp
```

## Parameters

| Parameter | Description |
|-----------|-------------|
| `name` | Tap in `user/repo` form (e.g., `hashicorp/tap`) |

## Actions

| Action | Command |
|--------|---------|
| install | `brew tap {{name}}` |
| update | None — taps refresh via `brew update` (skipped automatically) |
| uninstall | `brew untap {{name}}` |

## License

Licensed under either of

 * Apache License, Version 2.0
   ([LICENSE-APACHE](LICENSE-APACHE) or <http://www.apache.org/licenses/LICENSE-2.0>)
 * MIT license
   ([LICENSE-MIT](LICENSE-MIT) or <http://opensource.org/licenses/MIT>)

at your option.

## Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.
