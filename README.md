# edge-urid-playbook

Ansible tooling for automatically deploying Edge-URID to infrastructure of your choice.


## Getting started

* Check out this repo after making sure you've installed Ansible 2.12+

`git clone https://github.com/application-research/edge-urid-playbook`

* Edit the default inventory file (`inventories/production/hosts`) and list one or more machines you want to deploy to

* Set the following variables in `group_vars/all.yml`:
```
edge_main_dir: "/opt/edge"
compile_dir: "/usr/local/src/edge"
edge_binary_install_dir: "/usr/local/bin"
edge_blockstore_dir: "/mnt/mfs/services/whypfs/edge-urid/blocks"
edge_system_user: "estuary"
edge_system_group: "estuary"
edge_version: "main"                # The version of Edge to deploy
edge_admin_api_key: "REDACTED"      # The admin API key you wish to use

# env file stuff
edge_node_name: "ehi-edge-urid"
edge_description: "edge-urid running on Estuary Hosted Infrastructure."
delta_node_api: "https://delta.estuary.tech"
edge_shared_repo: "/mnt/mfs/services/whypfs/edge-urid"
edge_database_name: "edgeurid"
postgres_connection_string: "postgres://edge:REDACTED@postgres-ehi.estuary.tech:52432/edgeurid-db"
```

* Install dependencies

`ansible-galaxy install -r ./roles/requirements.yml`

None of these steps will need repeating once you've done them once (unless you want to update dependencies or they change).

* Run the playbook

`ansible-playbook -i ./inventories/production deploy.yml`


Ask in [#ecosystem-dev](https://filecoinproject.slack.com/archives/C016APFREQK) if you have any questions, and enjoy!


# TODOs/roadmap
* Add Docker deployment option, bare metal mode will be the default for now (and probably a long time, slightly more efficient I/O)
* Add PostgreSQL support beyond just a connection string option
