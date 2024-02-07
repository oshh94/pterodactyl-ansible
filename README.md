# pterodactyl-ansible
This is a quick and dirty Ansible playbook to install Pterodactyl using docker.

The Playbook has been tested on:
* Ubuntu 22.04

While it should be possible to run both the panel and wings on the same node, I haven't tested this and would not recommend that approach.

# Getting started
1. Install requirements from requirements.txt using `ansible-galaxy install -r requirements`.
2. Copy sample_inventory to inventory.
3. Update inventory/group_vars/all.yml. Ensure you set new safe values for passwords and hashid salt.
4. Run the playbook `ansible-playbook gameserver.yml -K`
5. Create an inital admin user for Pterodactyl:
```bash
docker exec -it panel bash
php artisan p:user:make
```


# Caveats
Beaware of the following caveats of the Playbook:
* The implementation of trafik is hardcoded to use Cloudflare.
* The playbook does some initial setup (like installing QEMU Guest agent, disable cloud-init manage_etc_hosts) which might not fit your use case. This should probably be moved out somewhere else.
* Multiple Ansible lint warnings.

# TODO
- [ ] Update Traefik to be generic (roles/traefik/defaults/main.yml).
- [ ] Resolve the above caveats.