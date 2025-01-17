# Stackdriver logger

A logger for Google's Stackdriver.\
We output JSON formatted logs compatible with Stackdriver.

## Usage
```rust
use stackdriver_logger;
use log::{error, info, trace, debug, warn};

fn main() {
    stackdriver_logger::init_with_cargo!();

    trace!("trace log");
    debug!("debug log");
    info!("info log");
    warn!("warn log");
    error!("error log");
}
```
Note that the `init_with_cargo!` macro will include your `Cargo.toml` in the resulting binary.
If you don't want that, check out the docs, a few more initializers are available.

## Behavior
When using the above macro, you don't have anything else to do.
For other initializers, you may need to provide two environment variables : `SERVICE_NAME` and `SERVICE_VERSION`.
We're using Cargo's `CARGO_PKG_NAME` and `CARGO_PKG_VERSION` as a fallback, but these are only available
if you run your application via Cargo. \
Check out the docs to see which initializers require environment variables.

## Enabling logging
This library accepts a `RUST_LOG` env variable, it works exactly like in [`env_logger`](https://github.com/sebasmagri/env_logger). \
By default, everything is disabled except for `error!`.
To enable all logs for your application :

```
RUST_LOG=your_application cargo run
```

For more details, take a look at the [env_logger docs](https://docs.rs/env_logger/0.6.0/env_logger/#enabling-logging).

## License
Licensed under either of

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or http://apache.org/licenses/LICENSE-2.0)
- MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

