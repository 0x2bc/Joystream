Tested Items
- Giza node installation

## NODE INSTALLATION

I was not able to install Giza node with setup.md manual.
I've tried on 2 different servers (Linode VPS and Contabo VPS), but have the same result. 

Server configs:
- Linode VPS  - Ubuntu 20.04.3 LTS
- Contabo VPS - Ubuntu 18.04.6 LTS


Got an error 

```

    error[E0658]: use of unstable library feature 'btree_retain'
     --> /root/.cargo/registry/src/github.com-1ecc6299db9ec823/serde_json-1.0.70/src/map.rs:263:18
      |
  263 |         self.map.retain(f);
      |                  ^^^^^^
      |
      = note: see issue #79025 <https://github.com/rust-lang/rust/issues/79025> for more information
      = help: add `#![feature(btree_retain)]` to the crate attributes to enable
```




Rust version downloaded with ./setup.sh command was  Rustc 1.56.1 (59eed8a2a 2021-11-01) on both servers. 


How I tried to fix the problem


#### Fixing Error: Attempt 1

Changed command
    WASM_BUILD_TOOLCHAIN=nightly-2021-03-24 cargo +nightly-2021-03-24 build --release 
To 
    WASM_BUILD_TOOLCHAIN=nightly-2021-03-24 cargo build --release
This didn't help. 

#### Fixing Error: Attempt 2
 
I manually installed cargo and rust and this didn't help. 

#### Fixing Error: Attempt 3
 
Using command  "cargo clean" and then installing rust manually with command "sudo apt install rustc" didn't help

#### Fixing Error: Attempt 4

Exclusion of "containerd" from setup.sh and it's manually installation didn't help. 


#### Fixing Error: Solutio

Finally I used the binary for the current chain and "chainspec-raw.json" file from /root/bin/.
This helped. 

#### General Info


My node named 0x2bc-giza-release is on the Telemetry website now https://telemetry.joystream.org/#list/Joystream%20Testnet%20giza-staging-october-21 






-- NOTE 2 --

Telemetry double entry
