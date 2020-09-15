# docker-learn-ocaml

[docker-compose.yml](https://docs.docker.com/compose/compose-file/) template for deploying [Learn-OCaml](https://github.com/ocaml-sf/learn-ocaml) in a VM.

## Overview

This configuration template combines several **Docker** containers to
deploy a [Learn-OCaml](https://github.com/ocaml-sf/learn-ocaml)
instance (version 0.13+), served in **HTTPS**, able to **send
e-mails** for account confirmation and password changes (assuming the
`use_passwd` option has been enabled), and communicating with a
**Moodle** server (hosted apart, e.g. in your university) using the
LTI protocol, allowing one to sign-up and sign-in very easily
(assuming both `use_moodle` and `use_passwd` options have been
enabled).

## Summary of the configuration steps

* Install `docker` [(see e.g. that page of docker-coq/wiki)](https://github.com/coq-community/docker-coq/wiki/CLI-usage#installing-docker)
* Install `docker-compose` [(see official doc)](https://docs.docker.com/compose/install/)
* Clone this repository using `git`.
* Edit the following files:
    * [.env](./.env)
    * [root-url.env](./root-url.env)
	* [reply-to.env](./reply-to.env)
	* [smtp.env](./smtp.env) (and create a text file `./secrets/smtp_password`)
* Run `docker-compose config` to check the configuration values.
* Run `docker-compose up` to start the server a first time.
* Check that the application is properly served using HTTPS.
* Run `docker-compose stop` (or `docker-compose down`).
* Uncomment line `STAGE: 'production'`in file [docker-compose.yml](./docker-compose.yml).
* Run `docker-compose up -d` to restart the server (`-d` = in background).
