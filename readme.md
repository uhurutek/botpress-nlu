# Botpress NLU

<img src="./readme.gif"/>

## Description

This repo contains every ML/NLU related code written by Botpress in the NodeJS environment.

The source code is structured in a mono-repo fashion using yarn workspaces. The `./packages` directory contains all available packages. The main packages are:

- [nlu-server](./packages/nlu-server/readme.md): Contains the Botpress Standalone NLU Server
- [lang-server](./packages/lang-server/readme.md): Contains the Botpress Language Server
- [nlu-cli](./packages/nlu-cli/readme.md): Small CLI to use as an entry point for both `nlu-server` and `lang-server`

Check out each individual packages for more details.

## Running from source

**Prerequisites**: Node 12.13 (you can use [nvm](https://github.com/creationix/nvm)) and Yarn.

1. Run `yarn` to fetch node packages.
1. Run `yarn build && yarn start` to build and start the Standalone NLU server.
1. You can also run `yarn dev` to run the NLU Server with [ts-node](https://github.com/TypeStrong/ts-node) however, trainings won't be parallelized on several threads.

## Running from pre-built binaries

New executable binary files are packaged at every release. You can download those directly on release page located [here](https://github.com/botpress/nlu/releases).

## ⚠️⚠️ Disclaimer ⚠️⚠️

The NLU Server does **not** enforce authentication in any way. This means it is completely exposed to many attacks. If you plan on using the nlu-server in your local Botpress setup, makes sure it is not publicly exposed. If you plan on exposing the NLU server, make sure it his hidden behind a reverse proxy which ensures a proper authentication. This reverse proxy should:

- Ensure each appId (`X-App-Id` header) is unique.
- Ensure a user with appId `user1` can't call the nlu server with header `X-App-Id` set to anything other than `user1`.
- Ensure only calls with a registered appId can call the nlu server except maybe for the `GET /info` route.

The NLU Server's only purpose is to do NLU.

## Licensing

Different licences may apply to differents packages of the [./packages](https://github.com/botpress/nlu/tree/master/packages) directory. If no licence is specified, the package is protected by the same license as the [v12 Botpress repository](https://github.com/botpress/v12).
