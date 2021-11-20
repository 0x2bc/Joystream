### Scope Of Testing

1) Giza Node (DONE)
2) Storage Node 
3) Distribution Node 
4) CLI Commands
5) Others

### 1. Giza Node

#### Summary

I was not able to install Giza node using `setup.md` manual. Specifically I was stuck at the following step `WASM_BUILD_TOOLCHAIN=nightly-2021-03-24 cargo +nightly-2021-03-24 build --release`

I've tried on 2 different servers (Linode VPS and Contabo VPS), but with no luck. I've tried to fix the problem in different ways (see `Detailed Info` section) but nothing helped me. 

I've used on 2 different servers with the following configs:
- Linode VPS  - Ubuntu 20.04.3 LTS
- Contabo VPS - Ubuntu 18.04.6 LTS 
    CPU: 10 vCPU Cores
    RAM: 60 GB RAM
    STORAGE: 1.6 TB SSD

Names of my nodes on the Telemetry website:
- 0x2bc-giza-release
- 0x2bc-giza-release-2nd-node


#### Detailed Info

Following  `setup.md` manual on the step  `WASM_BUILD_TOOLCHAIN=nightly-2021-03-24 cargo +nightly-2021-03-24 build --release` I've got an error 

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


On my both servers rust version that was downloaded with  `./setup.sh` command was `Rustc 1.56.1 (59eed8a2a 2021-11-01)`. 

I've made different approaches to fix this problem


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


#### Fixing Error: Solution

Finally I used the binary for the current chain and "chainspec-raw.json" file from /root/bin/.
This helped. 


### 2. Storage Node

TBD

### 3. Distribution Node 

TBD

### 4. CLI Commands

TBD

### 5. Others

TBD

