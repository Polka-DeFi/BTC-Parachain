# Exchange Rate Oracle

Based on the Exchange Rate Oracle specification [https://interlay.gitlab.io/polkabtc-spec/spec/oracle.html](https://interlay.gitlab.io/polkabtc-spec/spec/oracle.html).

## Installation

Run `cargo build` from the root folder of this directory.

## Testing

Run `cargo test` from the root folder of this directory.


## Integration into Runtimes

### Runtime `Cargo.toml`

To add this pallet to your runtime, simply include the following to your runtime's `Cargo.toml` file:

```TOML
[dependencies.btc-relay]
default_features = false
git = '../creates/exchange-rate-oracle'
```

and update your runtime's `std` feature to include this pallet:

```TOML
std = [
    # --snip--
    'exchange-rate-oracle/std',
]
```

### Runtime `lib.rs`

You should implement it's trait like so:

```rust
/// Used for test_module
impl ExchangeRateOracle::Trait for Runtime {
	type Event = Event;
}
```

and include it in your `construct_runtime!` macro:

```rust
ExchangeRateOracle: exchange-rate-oracle::{Module, Call, Storage, Event},
```

## Reference Docs

You can view the reference docs for this pallet by running:

```
cargo doc --open
```
