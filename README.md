### Prerequisites

1. Node.js - I recommend installing Node using either [nvm](https://github.com/nvm-sh/nvm) or [fnm](https://github.com/Schniz/fnm)

2. Solana Tool Suite - You can see the installation instructions [here](https://docs.solana.com/cli/install-solana-cli-tools). _note - I had a very hard time getting everything working on an M1 Mac, mainly `solana-test-validator` and `cargo-build-bpf`. I finally figured it out, and posted my solution [here](https://github.com/project-serum/anchor/issues/95#issuecomment-913090162). I'm sure at some point this will be fixed and work out of the box._

3. Anchor - Anchor installation was pretty straight-forward for me. You can find the installation instructions [here](https://project-serum.github.io/anchor/getting-started/installation.html).


### To build

1. Clone the repo

```sh
git clone git@github.com:anmoldh121/solana-counter.git
```

2. Change into the project directory you'd like to run

3. Install the dependencies

```sh
npm install
```

4. Start a local Solana node

```sh
solana-test-validator
```

5. Build the anchor project

```sh
anchor build
```

6. Fetch the project ID for the build:

```sh
solana address -k target/deploy/<programname>-keypair.json
```

6. Update the project ID in the Rust program located at __projectname/programs/src/programname.rs__ with the output from above.

7. Run the tests

```sh
anchor test
```

8. Change into the __app__ directory and install the dependencies:

```sh
cd app && npm install
``` 

9. Run the client-side app

```sh
npm start
```