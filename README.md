# MassNet Miner

[![Build Status](https://travis-ci.org/massnetorg/MassNet-miner.svg)](https://travis-ci.org/massnetorg/MassNet-miner) [![MIT](https://img.shields.io/badge/license-MIT-brightgreen.svg)](./LICENSE)

`MassNet Miner` is a Golang implementation of MassNet full-node miner.

## Requirements

[Go](http://golang.org) 1.13 or newer.

## Development

### Build from Source

#### Linux/Darwin

- Clone source code to `$GOPATH/src/github.com/massnetorg/MassNet-miner`.
- Go to project directory `cd $GOPATH/src/github.com/massnetorg/MassNet-miner`.
- Run Makefile `make build`. An executable `massminerd` would be generated in `./bin/`.

#### Windows

- Clone source code to `$GOPATH/src/github.com/massnetorg/MassNet-miner`.
- Open terminal in `$GOPATH/src/github.com/massnetorg/MassNet-miner`.
- Require environment variable as `GO111MODULE="on"`.
- Run `go build -o bin/massminerd.exe`. An executable `massminerd.exe` would be generated in `./bin/`.

### Contributing Code

#### Prerequisites

- Install [Golang](http://golang.org) 1.13 or newer.
- Install the specific version or [ProtoBuf](https://developers.google.com/protocol-buffers), and related `protoc-*`:
  ```
  # libprotoc
  libprotoc 3.6.1
  
  # github.com/golang/protobuf 1.3.2
  protoc-gen-go
  
  # github.com/gogo/protobuf 1.2.1
  protoc-gen-gogo
  protoc-gen-gofast
  
  # github.com/grpc-ecosystem/grpc-gateway 1.9.6
  protoc-gen-grpc-gateway
  protoc-gen-swagger
  ```

#### Modifying Code

- New codes should be compatible with Go 1.13 or newer.
- Run `gofmt` and `goimports` to lint go files.
- Run `make test` before building executables.

#### Reporting Bugs

Contact MASS community via community@massnet.org, and we will get back to you soon.

#### Verifying Commits

The following keys maybe trusted to commit code.

| Name | Fingerprint |
|------|-------------|
| massnetorg | A8A9 5C74 1AB8 08D3 E6E6  5B6C F8A8 D5CF 14D0 C419 |

## Documentation

### API

A documentation for API is provided [here](api/README.md).

### Transaction Scripts

A documentation for Transaction Scripts is provided [here](docs/script_en.md).

### Start minder

1: Set config file network->p2p->seeds to your custom eg.

"seeds": "192.168.10.2,192.168.",

2: remove the config file minder content

3: create a wallet address like this 
ms1qq59t8fv03c3fqvcy5e2jn5fcaleeet5temy992pmcya5pmwfwcp8qd3rm7y

4: set miner space size run follow commond set minder address is ms1qq59t8fv03c3fqvcy5e2jn5fcaleeet5temy992pmcya5pmwfwcp8qd3rm7y and size is 1024M:

curl -H "Content-Type:application/json" -X POST -d '{"payout_addresses":["ms1qq59t8fv03c3fqvcy5e2jn5fcaleeet5temy992pmcya5pmwfwcp8qd3rm7y"],
"capacity":1024,"passphrase":"123456"}' http://127.0.0.1:9686/v1/spaces

if the server tips you the minder is runing run this commond: 

curl -H "Content-Type:application/json" -X POST -d '{}' http://127.0.0.1:9686/v1/spaces/stop
if set the addreess and size then run this commond:

curl -H "Content-Type:application/json" -X POST -d '{}' http://127.0.0.1:9686/v1/spaces/mine

## License

`MassNet Miner` is licensed under the terms of the MIT license. See LICENSE for more information or see https://opensource.org/licenses/MIT.
