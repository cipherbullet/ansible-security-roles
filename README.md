---
title: "Ansible Security Roles"
---

# Ansible Security Roles

This repository contains a collection of Ansible roles that can be used to perform security-related tasks on servers. These roles can help you automate the process of securing your servers and ensure that your infrastructure is always compliant with industry-standard security benchmarks.

<br>

## Requirements
* Ansible 2.9 or higher
* Python 3

<br>

## Getting started
To use these roles in your Ansible project, you can simply clone this repository into your project's `roles` directory:

```bash
git clone https://github.com/your_username/ansible-security-roles.git roles/security
```

`(Recommended)`: If you are creating a fresh Ansible playbook for yourself, I suggest to use python venv. Go to your Ansible playbook root directory and then:

```bash
python -m venv venv
source venv/bin/activate
pip install ansible
```
<br>

## Roles
The following roles are currently available in this repository:

* **cis:** This role implements the **CIS benchmark** security checks for Ubuntu operating systems.

You can add more roles to this section as you develop them.

<br>

## Usage
1. Create `inventories/hosts.ini` file containing your host groups. exp:

```bash
# This is the host group name that you can call in your playbooks.
[dev]

# The target IP address and some ansible connection configuration for each host.
1.1.1.1 ansible_user=ubuntu
1.1.1.2 
```

2. To use a role in your playbook, you can simply include it as follows in your Ansible project root directory:

```yaml
# playbook.yml
- name: Security Benchmarks
  # group name in your inventory file or use `all` for all hosts
  hosts: dev
  
  roles:
    - name: cis
      become: yes
      gather_facts: true
      # Ignores errors and continues executing the playbook for all tasks
      ignore_errors: true
```

3. Run your playbook:

```bash
ansible-playbook -i inventories/hosts.ini playbook.yml
```
<br>

## Contributing
Contributions are welcome! If you have an idea for a new role or want to improve an existing one, feel free to submit a pull request.

<br>

## License
This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).

Of course, feel free to modify this to suit your needs and add more information as necessary.
