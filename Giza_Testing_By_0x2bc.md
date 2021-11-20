# Overview 

Below is the result of testing Giza release provided by @0x2bc.

You can find the scope of testing in the "Scope Of Testing" section.

For testing purposes there were used two different servers with the following configs:
- Linode VPS  - Ubuntu 20.04.3 LTS
- Contabo VPS - Ubuntu 18.04.6 LTS  
        &nbsp;&nbsp;&nbsp;CPU: 10 vCPU Cores  
        &nbsp;&nbsp;&nbsp;RAM: 60 GB RAM  
        &nbsp;&nbsp;&nbsp;STORAGE: 1.6 TB SSD  

# Useful Links

Links related to Giza release:

- Web Interface  https://giza-staging-a.joystream.app/    
- Working Groups https://giza-staging-a.joystream.app/#/working-groups/    
- Telemetry https://telemetry.joystream.org/#list/Joystream%20Testnet%20giza-staging-october-21  
- GitHub Page https://github.com/Joystream/joystream/tree/giza_staging  

# Scope Of Testing

1) Giza Node (DONE)
2) Storage Node 
3) Distribution Node 
4) CLI Commands
5) Others

## Preliminary Work 

Create new profile on the Membership tab on the  https://giza-staging-a.joystream.app/ website. 

Please pay attention you need to ask Dev Team or Testing Team for test tokens in order to register an account. 

Configure your profile on the https://giza-staging-a.joystream.app/ website. 

> If you want to use full functionality of the website https://giza-staging-a.joystream.app/  you need to set the endpoint. 
> You can do that by clicking the JS logo in the top left and setting it to custom and putting in wss://giza-staging-a.joystream.app/rpc -- and then refresh

## 1. Giza Node

#### Summary

I was not able to install Giza node using `setup.md` manual. Specifically I was stuck at the following step: 

```WASM_BUILD_TOOLCHAIN=nightly-2021-03-24 cargo +nightly-2021-03-24 build --release```

I've tried on 2 different servers (Linode VPS and Contabo VPS), but with no luck. I've tried to fix the problem in different ways (see `Detailed Info` section) but nothing helped me. 

According to @bwhm there are three possible solution on this problem 

> we have three options:
> 1. Try more (bad)
> 2. Use an old commit (won't be the native runtime anyway)
> 3. Use the binary for the current chain

> I'd say three is fine.  https://github.com/Joystream/joystream/releases/download/v9.3.0/joystream-node-5.1.0-9d9e77751-x86_64-linux-gnu.tar.gz

I used the third option and that worked fine for me. 

Work around this problem:
1) Install binaries from Joystream master branch ` https://github.com/Joystream/joystream/tree/master/node ` 
2) Instead of the "old" config file `joy-testnet-5.json` use the new one `chainspec-raw.json` that work fine for Giza release 

Names of my nodes on the Telemetry website:
- 0x2bc-giza-release
- 0x2bc-giza-release-2nd-node

#### Detailed Info

I followed the  `setup.md` guide to install Giza node. On the step  

```WASM_BUILD_TOOLCHAIN=nightly-2021-03-24 cargo +nightly-2021-03-24 build --release``` 

I've got an error 

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

On my both servers I've downloaded Rust during  `./setup.sh` execution. On both servers Rust version was `Rustc 1.56.1 (59eed8a2a 2021-11-01)`. 

Below are description of my attempts to overcome the problem. 

#### Attempt 1

I changed command `WASM_BUILD_TOOLCHAIN=nightly-2021-03-24 cargo +nightly-2021-03-24 build --release` to `WASM_BUILD_TOOLCHAIN=nightly-2021-03-24 cargo build --release` This didn't help me. 

#### Attempt 2
 
I manually installed cargo and rust (not using rustup) and tried to proceed with the following command 

```WASM_BUILD_TOOLCHAIN=nightly-2021-03-24 cargo +nightly-2021-03-24 build --release```

This didn't help.  I re-installed them again and proceed with the guide. This didn't help as well.

#### Attempt 3
 
I used the command  `cargo clean` and then tried to install Rust manually with command ```sudo apt install rustc```. 
This didn't help me.

#### Attempt 4

I tried to exclude `containerd` command from the `setup.sh` script and manually install `containerd` component.
This didn't help me. 


#### Solution

Finally I used the binary for the current chain and `chainspec-raw.json` file from `/root/bin/`.
This worked fine. 


## 2. Storage Node

TBD

## 3. Distribution Node 

TBD

## 4. CLI Commands

TBD

## 5. Others

TBD

