# yggdrasilLabs Homebrew tap

This tap has the Homebrew formulas of [yggdrasilLabs](https://github.com/yggdrasilLabs).

## Install Minos

```sh
brew tap libkrun/krun
brew trust libkrun/krun
brew tap yggdrasilLabs/tap
brew trust yggdrasilLabs/tap
brew install yggdrasilLabs/tap/minos
minos host doctor
```

The formula builds `minos`, the `minos-vmm` helper, and the static `minos-guest` from source. It uses the
Rust toolchain that the Minos repository pins, and it installs that toolchain into the build directory. The build
takes some minutes. The formula signs the helper with the entitlements it must have.

`minos host doctor` must end with `result: every check passed`.

Minos works only with the libkrunfw release that it was built against. Pin it, so that `brew upgrade` does not
move it before a Minos release does:

```sh
brew pin libkrunfw
```

To build from the `main` branch of Minos:

```sh
brew install --HEAD yggdrasilLabs/tap/minos
```

See the [Minos README](https://github.com/yggdrasilLabs/minos#readme) for Docker, the price table, and the model
provider.

The formula is generated. Its source is `packaging/homebrew/minos.rb` in the Minos repository, and the Minos
release workflow writes `Formula/minos.rb` here on each version tag. Edit the source, not this copy.
