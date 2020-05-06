# Hacklith

I present you Hacking + Regolith made possible with <3

![](hacklith.png)

4 letters from the first word, 4 letters from the second word. Full symmetry achieved. Everyone likes symmetry.

Sounds cliché but I like it.

# Installation

Deploy vanilla Ubuntu Server 20.04 LTS with OpenSSH installed. Let's assume I've got mine like this:

* Hostname: `hacklith`
* Username: `ubuntu`
* Password: `hack4me`

## Adjust inventory

There are two places for now which needs your attention:

* `inventory` file
* `group_vars/all` file

In the former you need to fill the information about your machine. Ansible needs to know how to connect to it and so on. The latter is used for some installation scripts and you need to provide your non-root username. Probably with a UID of 1000.

### lvextend

There is a playbook for extending logical volume because ubuntu by default sets up only 4GB LV. If you leave it at `false`, you don't have to care about `vg_name` and `lv_name` (just leave it as is).

## Run

You can either run the ansible playbook from the other machine or directly from the Ubuntu.

```bash
cd ansible && ansible-playbook --inventory inventory site.yml
```

