# roux.rs

[![CircleCI](https://circleci.com/gh/halcyonnouveau/roux.rs.svg?style=svg)](https://circleci.com/gh/halcyonnouveau/roux.rs)
[![Documentation](https://img.shields.io/badge/documentation-available-green.svg)](https://docs.rs/roux)
[![Crate](https://img.shields.io/crates/v/roux.svg)](https://crates.io/crates/roux)
![GitHub](https://img.shields.io/github/license/halcyonnouveau/roux.rs.svg)

A simple, asynchronous Reddit API wrapper implemented in Rust.

## Usage

### Using OAuth

To create an OAuth client with the Reddit API, use the `Reddit` class.
```rust
use roux::Reddit;
let client = Reddit::new("USER_AGENT", "CLIENT_ID", "CLIENT_SECRET")
    .username("USERNAME")
    .password("PASSWORD")
    .login()
    .await;

let me = client.unwrap();
```
It is important that you pick a good user agent. The ideal format is
`platform:program:version (by /u/yourname)`, e.g. `macos:roux:v0.3.0 (by /u/beanpup_py)`.
This will authticate you as the user given in the username function.

### Usage
Using the OAuth client, you can:

#### Submit A Text Post
```rust
use roux::Reddit;
let client = Reddit::new("USER_AGENT", "CLIENT_ID", "CLIENT_SECRET")
    .username("USERNAME")
    .password("PASSWORD")
    .login()
    .await;

let me = client.unwrap();
me.submit_text("TEXT_TITLE", "TEXT_BODY", "SUBREDDIT");
```

#### Submit A Link Post
```rust
use roux::Reddit;
let client = Reddit::new("USER_AGENT", "CLIENT_ID", "CLIENT_SECRET")
    .username("USERNAME")
    .password("PASSWORD")
    .login()
    .await;

let me = client.unwrap();
me.submit_link("LINK_TITLE", "LINK", "SUBREDDIT");
```

### Read-Only Modules

There are also read-only modules that don't need authentication:

* [Subreddits](https://docs.rs/roux/1.0.0/roux/subreddit/index.html)
* [Users](https://docs.rs/roux/1.0.0/roux/user/index.html)
