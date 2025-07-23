# Jinja Templating Engine
---
## Author Information
| Created by    | Created on | Version | Last Updated On | Pre Reviewer | L0 Reviewer | L1 Reviewer | L2 Reviewer |
|---------------|-------------|---------|------------------|----------------|---------------|----------------|---------------|
| Divya Mishra  | 16-07-2025  | V 1.0   | 17-07-2025       | Siddharth     |               |                |               |
---
## Table of Contents
- [What is Jinja?](#what-is-jinja)
- [Why Use Jinja?](#why-use-jinja)
- [Installing Jinja](#installing-jinja)
- [Core Concepts](#core-concepts)
  - [Variable Substitution](#variable-substitution)
  - [Using Default Filter](#using-default-filter)
  - [Conditionals with Jinja](#conditionals-with-jinja)
  - [Loops with Jinja](#loops-with-jinja)
  - [Accessing Host IP using hostvars](#accessing-host-ip-using-hostvars)
- [Jinja Templating in Ansible](#jinja-templating-in-ansible)
- [Use Cases](#use-cases)
- [Best Practices](#best-practices)
- [Conclusion](#conclusion)
- [Contact Information](#contact-information)
- [References](#references)
---
## What is Jinja?
Jinja is a high-performance templating engine for Python. It allows you to combine static text (like HTML, YAML) with variables and logic (like loops and conditions). When rendered, the template replaces variables with actual values and evaluates expressions to generate dynamic output.
---
## Why Use Jinja?
- **Separation of Logic and Layout**: Keep code and content separate.
- **Dynamic Content**: Insert variables, use conditions and loops.
- **Reusability**: Use includes, macros, and inheritance.
- **Web Development**: Used in frameworks like Flask.
- **Automation**: Popular in tools like Ansible for configuration generation.
---
## Installing Jinja
You can install **Jinja2** using `pip`.
| Platform | Command                         |
|----------|----------------------------------|
| Windows  | `py -m pip install jinja2`      |
| Linux    | `python3 -m pip install jinja2` |
> **Note:** No need to install Jinja separately when using Ansible. It comes pre-included.
---
## Core Concepts
### Variable Substitution
```yaml
- debug:
    msg: "Hello {{ user_name }}"
````
### Using Default Filter
```yaml
- debug:
    msg: "User: {{ user_name | default('guest') }}"
```
### Conditionals with Jinja
```yaml
- name: Conditionally install package
  apt:
    name: nginx
    state: present
  when: ansible_os_family == "Debian"
```
### Loops with Jinja
```yaml
- name: Create users
  user:
    name: "{{ item }}"
    state: present
  loop:
    - user1
    - user2
```
### Accessing Host IP using hostvars
```yaml
- debug:
    msg: "IP is {{ hostvars['hostname1']['ansible_host'] }}"
```
---
## Jinja Templating in Ansible
Ansible automatically uses Jinja2 for variable substitution.
**Example:**
```yaml
- name: Create a user
  hosts: localhost
  vars:
    username: myuser
  tasks:
    - name: Add user using Jinja template
      user:
        name: "{{ username }}"
        state: present
```
**Another Example – IP from tag-based host:**
```yaml
- name: Print webserver IP
  hosts: tag_Role_web
  gather_facts: no
  tasks:
    - debug:
        msg: "Webserver IP is {{ hostvars[inventory_hostname]['ansible_host'] }}"
```
---
## Use Cases
| Use Case                  | Description                                      |
| ------------------------- | ------------------------------------------------ |
| Flask HTML Templating     | Insert dynamic data into HTML templates          |
| Ansible Config Generation | Create YAML/INI/JSON configs using variables     |
| Email Template Rendering  | Use user data for newsletters or OTP emails      |
| YAML/JSON File Generation | Auto-generate deployment or cloud resource files |
| Log or Report Formatting  | Create readable logs or reports from raw data    |
| Shell Script Templating   | Use templates to insert values into `.sh` files  |
| Document Auto-Fill        | Populate repeated text blocks in documentation   |
---
## Best Practices
* Use clear and meaningful variable names to improve readability.
* Avoid complex logic inside templates. Keep templates focused on structure.
* Always use default filters to avoid undefined variable errors.
* Use `{% include %}` and `{% import %}` to reuse and organize code.
* Maintain consistent indentation and formatting across all templates.
---
## Conclusion
Jinja is a powerful and flexible templating engine that works well for both web development (like Flask) and automation tasks (like Ansible). It makes your templates dynamic using variables, conditions, loops, and reusability features like includes and macros.
---
## Contact Information
| **Name**     | **Email Address**                                                                 |
| ------------ | --------------------------------------------------------------------------------- |
| Divya Mishra | [divya.mishra.snaatak@mygurukulam.co](mailto:divya.mishra.snaatak@mygurukulam.co) |
---
## References
| **Link**                                                                                                        | **Description**                            |
| --------------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| [Jinja2 Official Documentation](https://jinja.palletsprojects.com/en/3.1.x/)                                    | Official documentation for Jinja2          |
| [Python Jinja2 Template Guide](https://docs.python.org/3/library/string.html#string.Template)                   | Python’s built-in string templating docs   |
| [Ansible Jinja2 Templating Guide](https://docs.ansible.com/ansible/latest/user_guide/playbooks_templating.html) | Guide on using Jinja2 in Ansible playbooks |
