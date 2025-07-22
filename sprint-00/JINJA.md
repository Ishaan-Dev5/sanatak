# Jinja Templating Documentation

---

### Author Information

| Author      | Created on  | Version    |   Last updated on | Internal Reviewer | L0 Reviewer  | L1 Reviewer | L2 Reviewer      |
|-------------|-------------|------------|-----------------|----------------|-------------------|---------------|----------------------------------|
| Ishaan    | 20-07-25    | v1.0  |       20-07-25       | Rohit Chopra    |  Akshit/Nitik    | Taran        | Abhishek Dubey/ Rishab sharma |


---

## Table of Contents 

1. [Introduction](#1-introduction)
2. [What is Jinja2](#2-what-is-jinja2)
3. [Why we use jinja2 template](#3-Why-we-use-jinja2-template)
4. [Where It's Used in Ansible](#4-where-its-used-in-ansible)
5. [Use jinja2 in ansible](#5-use-jinja2-in-ansible)
6. [Advantages of Jinja2 Templates](#6-advantages-of-jinja2-templates)
7. [Disadvantages of Jinja2 Templates](#7-Disadvantages-of-jinja2-templates)
8. [Conclusiopn](#8-conclusion)
9. [FAQs](#9-FAQs)
10. [Contact Information](#10-contact-information)
11. [References](#11-references)

---

## 1. Introduction


---

## 2. What is Jinja2
Jinja2 is a powerful templating engine for Python used in Ansible to dynamically generate configuration files, templates, and scripts. It allows you to inject variables, use logic (like loops and conditionals), and perform filters on data within YAML or template files.

---

## 3. Why we use jinja2 template?

| Feature                | Description                                                        |
|------------------------|---------------------------------------------------------------------|
| Dynamic Configuration  | Create files or settings that adapt based on variable values.       |
| Avoid Redundancy       | Templates reduce repetition by letting you reuse logic.             |
| Powerful Filters       | Format strings, dates, lists, and more.                             |
| Logic Support          | Includes conditionals, loops, etc.                                  |



---

## 4. Where It's Used in Ansible

| Use Case        | Example Location           | Description                                 |
|-----------------|----------------------------|---------------------------------------------|
| Playbooks       | .yml                    | Inject variables or use conditionals        |
| Templates       | templates/*.j2         | Generate dynamic configuration files        |
| Roles           | roles/<role>/templates/  | Reusable templates for services/apps        |
| Handlers, Tasks | tasks/main.yml          | Use conditionals, filters                   |

---

## 5. Use jinja2 in ansible

1. Templates are used with the template: module in playbooks.
```
   project/
   ├── templates/
   │   └── nginx.conf.j2
   └── playbook.yml
```
2. Create a Template File (nginx.conf.j2)
```
  server {
    listen 80;
    server_name {{ domain_name }};

    location / {
        proxy_pass http://{{ backend_host }}:{{ backend_port }};
    }
}

```

3. playbook.yaml
```
  - name: Render Nginx config from Jinja2 template
  hosts: webserver
  become: true
  vars:
    domain_name: example.com
    backend_host: 127.0.0.1
    backend_port: 8080
  tasks:
    - name: Deploy nginx config
      template:
        src: templates/nginx.conf.j2
        dest: /etc/nginx/sites-available/{{ domain_name }}
        owner: root
        group: root
        mode: '0644'

```
 4. Run the playbook
```
ansible-playbook -i inventory playbook.yml
```


## 6. Advantages of Jinja2 Templates

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
## 7. Disadvantages of Jinja2 Templates

| Disadvantage                 | Description                                                                 |
|-----------------------------|-----------------------------------------------------------------------------|
| **Debugging Complexity**    | Errors in templates can be hard to trace, especially in large or nested files. |
| **Learning Curve**          | Beginners may struggle with Jinja syntax, especially when combined with Ansible logic. |
| **Error-Prone with Undefined Variables** | Templates fail if variables aren't defined and `default()` isn't used. |

---
## 8. Conclusion

---

## 9. FAQs

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

## 10. Contact Information
| Name         | Email address          |
|--------------|------------------------|
| Ishaan         | ishaan.aggarwal.snaatak@mygurukulam.co    |

## 11. References
| Links                                             | Descriptions                                                    |
|---------------------------------------------------|-----------------------------------------------------------------|
| jinja2 officail docs| [Visit](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_templating.html)                      |
| templating with jinja 2|  [Visit](https://medium.com/@vinoji2005/day-12-templating-with-jinja2-enhancing-ansible-automation-cfe1be1b5d72)              |
