## Install Rust and the Rust toolchain

#####  1.Install `rustup` by running the following command: 

` curl https://sh.rustup.rs -sSf | sh `

##### 2.Configure your current shell to reload your PATH environment variable so that it includes the Cargo `bin` directory by running the following command: 

` source ~/.cargo/env `

##### 3.Configure the Rust toolchain to default to the latest `stable` version by running the following commands: 

`rustup default stable`

`rustup update`

##### 4. Add the `nightly` release and the `nightly` WebAssembly (`wasm`) targets by running the following commands: 

`rustup update nightly`

`rustup target add wasm32-unknown-unknown --toolchain nightly`

##### 5. Verify your installation by running the following commands: 

`rustc --version`
`rustup show`

## Setup HexSpaceSocialGraph Protocol Node

### 1. Installing The Substrate Contracts Node

 We need to use a Substrate node with the built-in `pallet-contracts` pallet. For this workshop we'll use a pre-configured Substrate node client. 

`cargo install contracts-node --git https://github.com/paritytech/substrate-contracts-node.git --tag v0.3.0 --force --locked`

### 2. ink! CLI

```
# For Ubuntu or Debian users
sudo apt install 
# For MacOS users
brew install binaryen
```

#### cargo-contract

`cargo install cargo-contract --vers 0.15.0 --force --locked`

### 3. Running a Substrate Smart Contracts Node

` substrate-contracts-node --dev  `



## Setup Contracts

HexSpaceSocialGraph Protocol Contracts are provided in `https://github.com/rust-0x0/5degrees-protocol-substrate/tree/dev`. 

It's developed with ink!.

### Get contracts

```
git clone -b dev https://github.com/rust-0x0/5degrees-protocol-substrate.git
```


## Compile contracts from source code

The HexSpaceSocialGraph-Protocol provides script to simplify the contract compilation process while collecting the editing results into a unified directory to facilitate contract deployment and usage. Execute in the project root directory

```bash
bash ./build-all.sh
```

All contract compilation results are saved in the release directory.

### Compile  one by one 

##### compile

` cargo  contract build`

In HexSpaceSocialGraph project 

like cd erc1155/       


## Deploy

The HexSpaceSocialGraph Protocol creates the substrate chain to connect the POLKADOT Ecology, and all contracts are deployed on the HexSpaceSocialGraph dev node. This section explains how to make use of Polkadot JS App to deploy contracts.

Use `https://polkadot.js.org/apps/` upload target/ink .contract file to deploy contract.

#### 1.set the node IP and port ( `ws://127.0.0.1:9944` default).

![](./1.png)

#### Upload & Deploy contracts

Enter `Developer-> Contracts` and click Upload & deploy code.

![](./2.jpg)

Select the contract files that required to deploy contract.

![](./3.jpg)

After you upload the contracts, you can instantiate the contract on the chain. In substrate, you need to perform the contract’s initialization function, usually new or the default function.

![](./4.jpg)

Select the initialization function call, fill in the initialization parameters, set the main contract administrator, and set the contract initial balance, click `Deploy`.
click `Deploy `, and `Submit and Sign`

## Initialization

![](./5.jpg)

Deploy HexSpace.

![](./6.jpg)

# Setup HexSpaceSocialGraph Protocol Front-end

## Install `Polkadot JS Extension`

Please install `Polkadot JS Extension` before you start. You can get it from here https://polkadot.js.org/extension/

### Get source code

Please get the code from `https://github.com/rust-0x0/5degrees-protocol-front-end/tree/dev`

```
git clone -b dev https://github.com/rust-0x0/5degrees-protocol-front-end.git
```

### Config front-end

#### 1. Replace contract address

![](./front-1.jpg)

![](./front-3.jpg)

Please find the correct contract address in `.env `, and update the correct  contract address in   ```.env ```. 



#### 3. Replace connect path

And replace `.env REACT_APP_PROVIDER_SOCKET` to your connect path.

it should be `ws://127.0.0.1:9944` by default.


### Install dependencies

Run `yarn ` to install packages needed for this App.

### Start front-end

`yarn start` runs the app in the development mode.
Open http://localhost:8100 to view it in the browser.



##### Get gas from ALICE

In `https://polkadot.js.org/apps` Account page, use account  send gas to your extension account.



## Acknowledgements

It is inspired by existing projects & standards:

- [5degrees](https://github.com/5DegreesProtocol/5degrees-protocol.git)


NOTE: This pallet implements the aforementioned process in a simplified way, thus it is intended for demonstration purposes and is not audited or ready for production use.

## Upstream

This project was forked from
- [the Substrate Contracts node](https://github.com/paritytech/substrate-contracts-node.git).
- [the Substrate DevHub Front-end Template](https://github.com/substrate-developer-hub/substrate-front-end-template)
