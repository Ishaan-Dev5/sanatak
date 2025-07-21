# Jinja Templating Documentation

---

| Author      | Created on  | Version    | Last updated by | Last edited on |
|-------------|-------------|------------|-----------------|----------------|
| Ishaan    | 20-07-25    | version 1  | Ishaan        | 20-07-25       |

---

## Table of Contents 

- [Introduction](#what-is-jinja2)
- [Why we use jinja2 template](#Why-we-use-jinja2-template)
- [Advantages of Jinja2 Templates](#advantages-of-jinja2-templates)
- [Disadvantages of Jinja2 Templates](#Disadvantages-of-jinja2-templates)
- [FAQs](#FAQs)
- [Contact Information](#contact-information)
- [References](#references)

---

## What is Jinja2
Jinja2 is a powerful templating engine for Python used in Ansible to dynamically generate configuration files, templates, and scripts. It allows you to inject variables, use logic (like loops and conditionals), and perform filters on data within YAML or template files.

---

## Why we use jinja2 template?

| Feature                | Description                                                        |
|------------------------|---------------------------------------------------------------------|
| Dynamic Configuration  | Create files or settings that adapt based on variable values.       |
| Avoid Redundancy       | Templates reduce repetition by letting you reuse logic.             |
| Powerful Filters       | Format strings, dates, lists, and more.                             |
| Logic Support          | Includes conditionals, loops, etc.                                  |



---

###  Where It's Used in Ansible

| Use Case        | Example Location           | Description                                 |
|-----------------|----------------------------|---------------------------------------------|
| Playbooks       | .yml                    | Inject variables or use conditionals        |
| Templates       | templates/*.j2         | Generate dynamic configuration files        |
| Roles           | roles/<role>/templates/  | Reusable templates for services/apps        |
| Handlers, Tasks | tasks/main.yml          | Use conditionals, filters                   |

---

### Use jinja2 in ansible
1. Templates are used with the template: module in playbooks.
```
   project/
   ├── templates/
   │   └── hello.j2
   └── playbook.yml
```
2. Create a Template File (hello.j2)
```
   Hello, {{ name }}!
   {% if is_admin %}
   You have admin access.
   {% else %}
   You are a regular user.
   {% endif %}
```
   This file contains:
- {{ name }} — **a variable**
- {% if %} — **a control structure**

3. playbook.yaml
```
   - name: Render Jinja2 template
     hosts: localhost
     vars:
       name: Ishaan
       is_admin: true
     tasks:
       - name: Create file from template
         template:
             src: templates/hello.j2
             dest: /tmp/hello.txt

```
 4. Final Output (/tmp/hello.txt)
```

    Hello, Ishaan!
    You have admin access.

```


## Advantages of Jinja2 Templates

| Advantage                     | Description                                                                 |
|------------------------------|-----------------------------------------------------------------------------|
| **Dynamic Content Generation** | Templates adapt based on variable input, enabling flexible configurations.  |
| **Seamless Integration with Ansible** | Used directly in playbooks and roles with `template:` module.              |
| **Clean Syntax**             | Python-like syntax is readable and easy to learn.                           |
| **Supports Logic**           | Full control structures like `if`, `for`, and `else` enable complex logic.  |
| **Lightweight & Fast**       | Efficient rendering even for large files or many variables.                 |
| **Error Handling**           | Features like `default()` help avoid runtime errors from missing values.    |
| **Tool-Agnostic**            | Can be used in web frameworks (like Flask, Django) as well as tools like Ansible, SaltStack, etc. |

---
## Disadvantages of Jinja2 Templates

| Disadvantage                 | Description                                                                 |
|-----------------------------|-----------------------------------------------------------------------------|
| **Debugging Complexity**    | Errors in templates can be hard to trace, especially in large or nested files. |
| **Learning Curve**          | Beginners may struggle with Jinja syntax, especially when combined with Ansible logic. |
| **Error-Prone with Undefined Variables** | Templates fail if variables aren't defined and `default()` isn't used. |

---

## FAQs

### 1.What is Jinja2?
Jinja2 is a Python-based templating engine that lets you embed variables, logic, and filters in text files. It is used by Ansible to generate dynamic files like configuration files, scripts, and templates.



### 2.What file extension should Jinja2 templates have?
Templates usually use the .j2 extension to indicate they are Jinja2-based, e.g., nginx.conf.j2.



### 3.  How do I use a Jinja2 template in an Ansible playbook?
Use the template: module in your playbook like this:

yaml
```
Copy
Edit
- name: Render config
  template:
    src: nginx.conf.j2
    dest: /etc/nginx/nginx.conf
```


---

## Contact Information
| Name         | Email address          |
|--------------|------------------------|
| Ishaan         | ishaan.aggarwal.snaatak@mygurukulam.co    |

## References
| Links                                             | Descriptions                                                    |
|---------------------------------------------------|-----------------------------------------------------------------|
| https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_templating.html | jinja2 officail docs                      |
|  https://medium.com/@vinoji2005/day-12-templating-with-jinja2-enhancing-ansible-automation-cfe1be1b5d72               | templating with jinja 2|
