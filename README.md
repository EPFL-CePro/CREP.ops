# CREP.ops
This repository regroups the configuration-as-code for the [CREP] project.
It is used to deploy CREP in [production] or [test] version.
It uses [Ansible] wrapped in a [suitcase] called [`crepsible`](./crepsible).

## Prerequisites
- Access to the [Keybase] team `/keybase/team/cepro_crep/`
- Access to the prod & test VMs (as root)

## How it works
`./crepsible`
- Install some dependencies on the VM (Docker, Node, NPM, ...)
- Setup the database on the running MySQL server
- Clone the git repository, copy the env variables from Keybase, build the Docker image and run CREP's container
- Configurate Apache

Use `./crepsible --prod` to deploy on the production VM.

### Tags
- `crep.setup`
    - Install necessary dependencies on the VM
- `crep.database`
    - Setup the database on the running MySQL server
- `crep.run`
    - Clone the git repository, and do the necessary to start the project (docker image & container) : This is mostly what you want to do if you just made some changes to the project that you want to push in production.
- `crep.apache`
    - Configurate Apache & certificates (certificate are on the Keybase)

To use a tag : `./crepsible -t crep.setup` or `./crepsible --prod -t crep.setup`


[Ansible]: https://ansible.com/
[CREP]: https://github.com/epfl-cepro/crep/
[Keybase]: https://keybase.io/
[production]: https://crep.epfl.ch/
[suitcase]: https://github.com/epfl-si/ansible.suitcase/
[test]: https://crep-test.epfl.ch/