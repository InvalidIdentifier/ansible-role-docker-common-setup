# Ansible Role: Docker Common Setup

This Ansible role installs and configures Docker on Debian-based systems. It ensures that Docker Engine, CLI, Containerd, and related plugins are installed and properly configured.

## Requirements

- Ansible 2.9+
- Debian-based operating system

## Role Variables

| Variable         | Default Value           | Description                                     |
|------------------|-------------------------|-------------------------------------------------|
| `bindmount_dir`  | `/data/bindmounts`    | Directory path for bind-mount                   |
| `ansible_user`   | `{{ ansible_user }}`    | The user to be added to the Docker group        |

## Dependencies

No dependencies on other roles.

## Example Playbook

```yaml
- hosts: servers
  become: yes
  roles:
    - role: ansible-role-docker-common-setup
```

## Tasks

### Install Required Packages
Installs essential packages like `ca-certificates`, `curl`, `gnupg`, and `lsb-release`.

### Create Directory for GPG Keys
Creates a directory to store the GPG keys of docker and ctop.

### Download Docker Official GPG Key
Downloads Docker's GPG key for repository verification.

### Add Docker Apt Repository
Adds Docker's repository to apt sources.

### Download ctop GPG Key
Downloads ctop GPG key for repository verification.

### Add ctop Repository
Adds ctop repository to apt sources.

### Update Apt Package Index
Updates the apt package index to reflect the newly added Docker repository.

### Install Docker Engine, CLI, Containerd, and Plugins
Installs Docker Engine, CLI, Containerd, and related plugins and ctop.

### Ensure Docker Service is Running and Enabled
Ensures the Docker service is started and enabled to start at boot.

### Ensure Group Docker Exists
Ensures the Docker group exists.

### Add User to Docker Group
Adds the specified user to the Docker group.

### Alias for Docker Ps Command
Creates an alias `dops` for the `docker ps` command.

### Check and Create Bindmount Directory
Checks if the bind-mount directory exists and creates it if necessary.

### Check and Create Docker Network
Checks if the Docker network exists and creates it if necessary.