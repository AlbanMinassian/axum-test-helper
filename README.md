# axum-test-helper

`axum-test-helper` exposes [`axum`] original TestClient, which is private to the [`axum`] crate

More information about this crate can be found in the [crate documentation][docs].

## High level features

- Provide an easy to use interface
- Start a server in a different port for each call
- Deal with JSON, text and files response/requests

## Usage example

Add this crate as a dev-dependency:

```
[dev-dependencies]
axum-test-helper = "0.*" # alternatively specify the version as "0.2.0"
```

Use the TestClient on your own Router:

```rust
use axum::Router;
use axum::http::StatusCode;
use axum_test_helper::TestClient;

// you can replace this Router with your own app
let app = Router::new().route("/", get(|| async {}));

// initiate the TestClient with the previous declared Router
let client = TestClient::new(app);
let res = client.get("/").send().await;
assert_eq!(res.status(), StatusCode::OK);
```

You can find examples like this in
the [example directory][examples].

See the [crate documentation][docs] for way more examples.

## License

This project is licensed under the [MIT license][license].

[`axum`]: https://github.com/tokio-rs/axum/blob/405e3f8c44ce76c3922fa25db13491ea375c3e8e/axum/src/test_helpers/test_client.rs
[examples]: https://github.com/cloudwalk/axum-test-helper/tree/main/examples
[docs]: https://docs.rs/axum-test-helper
[license]: https://github.com/cloudwalk/axum-test-helper/blob/main/LICENSE
