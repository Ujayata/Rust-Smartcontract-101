# note

- This Rust code defines a basic note-taking canister for the Internet Computer, allowing users to manage notes through a set of functions.It also has a frontend that interacts with it.



- Users can interact with the canister to perform CRUD (Create, Read, Update, Delete) operations on notes.
- Functions such as get_note, add_note, update_note, and delete_note are provided for these operations.

To learn more before you start working with note, see the following documentation available online:

- [Quick Start](https://internetcomputer.org/docs/quickstart/quickstart-intro)
- [SDK Developer Tools](https://internetcomputer.org/docs/developers-guide/sdk-guide)
- [Rust Canister Devlopment Guide](https://internetcomputer.org/docs/rust-guide/rust-intro)
- [ic-cdk](https://docs.rs/ic-cdk)
- [ic-cdk-macros](https://docs.rs/ic-cdk-macros)
- [Candid Introduction](https://internetcomputer.org/docs/candid-guide/candid-intro)
- [JavaScript API Reference](https://erxue-5aaaa-aaaab-qaagq-cai.raw.icp0.io)

If you want to start working on your project right away, you might want to try the following commands:

```bash
cd note/
dfx help
dfx canister --help
```

## Running the project locally

If you want to test your project locally, you can use the following commands:

```bash
# Starts the replica, running in the background
dfx start --background

# Deploys your canisters to the replica and generates your candid interface
dfx deploy
```

Once the job completes, your application will be available at `http://localhost:4943?canisterId={asset_canister_id}`.

If you have made changes to your backend canister, you can generate a new candid interface with

```bash
npm run generate
```

at any time. This is recommended before starting the frontend development server, and will be run automatically any time you run `dfx deploy`.

If you are making frontend changes, you can start a development server with

```bash
npm start
```

Which will start a server at `http://localhost:8080`, proxying API requests to the replica at port 4943.

### Note on frontend environment variables

If you are hosting frontend code somewhere without using DFX, you may need to make one of the following adjustments to ensure your project does not fetch the root key in production:

- set`DFX_NETWORK` to `production` if you are using Webpack
- use your own preferred method to replace `process.env.DFX_NETWORK` in the autogenerated declarations
  - Setting `canisters -> {asset_canister_id} -> declarations -> env_override to a string` in `dfx.json` will replace `process.env.DFX_NETWORK` with the string in the autogenerated declarations
- Write your own `createActor` constructor
