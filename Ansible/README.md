# Ansible Playbook for Setting Up Docker and Kubernetes Manifests

This Ansible playbook is designed to set up Docker and deploy Kubernetes manifests using roles from [geerlingguy](https://github.com/geerlingguy).

## Prerequisites

- Ansible installed on the host machine.
- Access to the target hosts specified in the inventory file.

## Usage

1. Clone this repository:

    ```bash
    git clone https://github.com/gtkachenko/42cc.git
    ```

2. Navigate to the repository:

    ```bash
    cd Ansible/
    ```

3. Update the `hosts` file with your target host information.

4. Run the Ansible playbook:

    ```bash
    ansible-playbook -i hosts playbook.yml
    ```

## Playbook Structure

### Install Docker

The first part of the playbook installs Docker on all specified hosts.

```yaml
- hosts: all

  vars:
    pip_install_packages:
      - name: docker

  roles:
    - geerlingguy.pip
    - geerlingguy.docker
```

### Deploy Kubernetes Manifests
The second part of the playbook deploys Kubernetes manifests on the local machine.
```yaml
- hosts: localhost
  connection: local
  gather_facts: no

  vars:
    ansible_python_interpreter: "{{ ansible_playbook_python }}"
    k8s_kubeconfig: ~/.kube/config-k8s-cluster
    k8s_manifests_base_dir: ../Kubernetes
    k8s_manifests:
      - deployment

  roles:
    - role: geerlingguy.k8s_manifests

```
Adjust the variables such as k8s_kubeconfig and k8s_manifests_base_dir based on your setup.