Lab Setup Scripts
====

These are my setup scripts for my home-lab environment. It's designed 
for a small cluster of VMs/baremetal nodes running docker services.

For docker setup, the project enables [Docker Swarm](https://docs.docker.com/engine/swarm/) 
mode as well as
[Docker Stack](https://docs.docker.com/engine/reference/commandline/stack/)
to create lightweight services (as compared with Kubernetes).

# Contents

## Ansible Setup

- Install conda: [conda playbook](playbooks/conda.yaml)
- Docker setup: [docker playbook](playbooks/docker.yaml)

  It installs docker on each Ansible node.

- Docker Swarm setup; [docker swarm](playbooks/docker_swarm.yaml)

  It sets up the swarm mode, with leader labeled as "swarm_seed" and
  the followers "swarm_managers" in Ansible host configuration.

## Docker Services Setup

For docker setup, this project uses Docker Swarm mode to deploy
services to a cluster of nodes. Use the "docker service" or
"docker stack" command to create or manage docker swarm services.

E.g. deploy a new stack for dask cluster:

```
docker stack deploy dask-cluster -c dask.yaml
```

References:

- [Docker Stack command](https://docs.docker.com/engine/reference/commandline/stack/)
- [Docker Stack Mode](https://docs.docker.com/engine/swarm/stack-deploy/)
- [Docker Swarm Mode](https://docs.docker.com/engine/swarm/)

- Dask cluster setup: [docker stack deploy](docker/dask.yaml)