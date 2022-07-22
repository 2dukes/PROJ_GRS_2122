# Networks and Systems Management

The [labs](labs/) folder concerns practical classes and involves setting up load-balanced web servers, DHCP servers, monitoring systems like [Nagios](https://www.nagios.org/), proxies, firewalls, VPNs, DMZs, split-DNS, and routers. Along with that, all the necessary procedures to deal with the management of virtual networks were also explored. The [proj](proj/) folder contains the developed project, as detailed next. 

## A company's network

This project is a system for automatic deployment and testing of a company's
network. This company has 2 geographic locations: Porto, and Lisboa.

The company serves/develops a web application, which resides in Lisboa. The web
developers work there as well.

The company's network managers, who are responsible for managing/administrating
the network and services of the company, work in Porto.

### Docker containers

The [docker directory](proj/docker) contains the custom docker containers used by
the different services and clients on both networks.

For the purposes of this project, human clients are also represented by docker
containers. This is done for testing purposes.

### Machines

The configuration machine is the one that deploys files to the Porto and Lisboa
machines. Its files reside in the [config_machine directory](proj/config_machine).

The [lisboa_machine directory](proj/lisboa_machine) contains the network
source-of-truth (**nsot**), the services' configuration, and the tests specific
for the Lisboa part of the network.

The [porto_machine directory](proj/porto_machine) contains the network
source-of-truth (**nsot**), the services' configuration, and the tests specific
for the Porto part of the network.

## Pipeline

### Setup

The **setup phase** is the initial part of the pipeline. This phase can be run
with the [setup script](proj/setup.sh). This script takes 3 arguments:

- The network name (e.g.: porto or lisboa);
- The target machine ssh identifier (e.g.: vmb or vmc);
- A colon (`:`) separated list (like UNIX's `PATH` variable) of docker container
  names.

There are 2 scripts, [setup-lisboa.sh](proj/setup-lisboa.sh) and
[setup-porto.sh](proj/setup-porto.sh), that wrap the [setup script](proj/setup.sh) and
pass the needed arguments for the current setup.

### Deployment and testing

The 2 last phases of the pipeline, deployment and testing, are run by executing
the deploy script inside the respective machine directory, for example
[Lisboa's deploy script](proj/lisboa_machine/deploy.sh).

These scripts should be run through SSH, for example:
`ssh vmb bash < ./lisboa_machine/deploy.sh`

* Collaborators
    - Ana Barros up201806593@fe.up.pt
    - João Costa up201806560@fe.up.pt
    - João Martins up201806436@fe.up.pt
    - Rui Pinto up201806441@fe.up.pt
