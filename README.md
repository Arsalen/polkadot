Polkadot
=========

Overview
------------

A Polkadot development network comprised of six containerized validators (Alice, Bob, Charlie, Dave, Eve and Ferdie) equipped with a telemetry dashboard. 

About
------------

Polkadot is a sharding protocol which enable cross-blockchain communication.
- Transactions are spread across multiple parallel blockchains (relay and parachains).
- Derived from Substrate, a framework for building customizable Blockchains (p2p networking and cryptographic libraries out-of-the-box).
- Forkless upgrades through web-assembly state transition machines.
- Support of GRANDPA/BABE consensus algorithms which are a proof-of-stake variants.
- Pro-rata pay out of DOTs (native currency).
- An authentication system through public-key cryptography based on Curve25519.

Requirements
------------

- [Docker](https://docs.docker.com/engine/)
- [Docker compose](https://docs.docker.com/compose/)

Getting Started
------------

By default, each validator will make use of a secret key (stored within secrets/ folder) for p2p communication, you can though set your proper keys using Substrate's native keygen tool [subkey](https://substrate.dev/docs/en/ecosystem/subkey) and update the dotenv file with the proper address.

Nodes are pluggable, means that you can append/discard them as per your needs, note that each is implemented on a separate file to enable you easily attach/detach each in sequence starting from Alice then Bob and so on.

Telemetry is by default exposed on port 80, which may cause some issues when another service is running on the same port (nginx often), you can however change the ```EXPORTER_PORT``` value.

Run
```bash
docker-compose -f docker-compose.yml -f docker-compose.telemetry.backend.yml -f docker-compose.telemetry.frontend.yml -f docker-compose.alice.yml -f docker-compose.bob.yml -f docker-compose.charlie.yml -f docker-compose.dave.yml -f docker-compose.eve.yml -f docker-compose.ferdie.yml up -d
```
Then connect to ```http://localhost```

Note: In order to be able to deploy your network on a swarm service, you need to set the ```dev_net``` driver to support overlay networks.

References
------------------

- [Polkadot website](https://polkadot.network/)
- [Polkadot repository](https://github.com/paritytech/polkadot)