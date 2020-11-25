# terragrunt-atlantis-server
A simple project to build container images for Atlantis server bundled with Terragrunt, include with ansible playbook to deploy it.

## Prerequisites
* Terragrunt v0.23.20 (Server)
* Atlantis v0.12.0 (Server)
* Docker v19.03.6 (Server)
* Ansible v2.9.9 (Client)

## How To
1. Build the Atlantis with Terragrunt image
    ```bash
    $ docker build -t ardikabs/terrantis:0.1.0 -f builds/Dockerfile.terrantis
    $ docker push ardikabs/terrantis:0.1.0
    ```
1. Deploy the Atlantis with Terragrunt service
    ```bash
    $ cd terragrunt-atlantis-server
    $ cd ansible
    $ chmod 755 plays; cd plays
    $ ansible-playbook -i ../inventory/atlantis.ini -e "HOSTS=<your-machine-address>" deploy-atlantis.yaml
    ```