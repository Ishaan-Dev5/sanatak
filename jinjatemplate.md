# Jinja Templating Documentation

---

| Author      | Created on  | Version    | Last updated by | Last edited on |
|-------------|-------------|------------|-----------------|----------------|
| Ishaan    | 20-07-25    | version 1  | Ishaan        | 20-07-25       |

---

## Table of Contents 

- [Introduction](#what-is-gunicorn)
- [Why We need Gunicorn](#why-we-need-gunicorn)
- [Features](#Features-Of-Gunicorn)
- [Use Cases](#use-cases-of-gunicorn)
- [Advantages of Gunicorn](#advantages-of-gunicorn)
- [Disadvantages of Gunicorn](#Disadvantages-of-gunicorn)
- [FAQs](#FAQs)
- [Contact Information](#contact-information)
- [References](#references)

---

## What is Jinja2
Jinja2 is a powerful templating engine for Python used in Ansible to dynamically generate configuration files, templates, and scripts. It allows you to inject variables, use logic (like loops and conditionals), and perform filters on data within YAML or template files.

---

## Why we use jinja2 template?
| Dynamic Configuration    | Create files or settings that adapt based on variable values.       |
| Avoid Redundancy         | Templates reduce repetition by letting you reuse logic.             |
| Powerful Filters         | Format strings, dates, lists, and more.                             |
| Logic Support            |Includes conditionals, loops, etc.                                   |


---

## Deplyoment Before GUnicorn

Before the widespread use of Gunicorn, Python web applications were often deployed using a variety of methods, including: Flask's built-in development server (which is not suitable for production), other WSGI servers like Waitress or uWSGI, or directly through web servers like Apache or Nginx with a WSGI module

---


## Features of Gunicorn

|  Feature                  |  Description |
|----------------------------|----------------|
| **WSGI Compliance**        | Works well with Python web frameworks like Django, Flask, and FastAPI. |
| **Pre-Fork Worker Model**  | Uses multiple processes to handle many users at the same time. |
| **Supports Sync & Async**  | Can handle both normal and real-time tasks using special worker types (like `gevent`). |
| **Lightweight & Fast**     | Runs quickly and doesn't use too many system resources. |
| **Simple Configuration**   | Easy to set up using terminal commands or config files. |
| **Automatic Worker Management** | Automatically restarts or replaces stuck or slow workers. |
| **Production-Ready**       | Built to handle real user traffic on websites or apps. |
| **Framework Agnostic**     | Can be used with any Python web framework that follows WSGI. |
| **Integration Friendly**   | Works smoothly with tools like Nginx, HAProxy, or AWS Load Balancer. |
| **Extensible Hooks**       | Lets you add your own custom actions during server startup, shutdown, etc. |

---


##  Use Cases of Gunicorn

|  Use Case |  Description |
|-------------|----------------|
| **Run Python Web Apps** | Helps run Python websites made with Flask, Django, or FastAPI. |
| **For Live/Production Use** | Can handle real users and traffic, good for live websites. |
| **Handles Many Users** | Uses multiple workers to serve many users at the same time. |
| **Works with Nginx/Apache** | Often used behind Nginx or Apache, which handles static files and SSL. |
| **Used in Docker/Kubernetes** | Works well inside containers and cloud platforms for microservices. |
| **Serve APIs** | Can serve REST APIs quickly and handle many requests. |
| **Cloud-Friendly** | Works easily on AWS, GCP, Azure, and other cloud platforms. |
| **Simpler than uWSGI** | Easier to set up than uWSGI but does a similar job. |
| **Can Handle Async Tasks** | Supports long-running or real-time tasks using async workers. |
| **Used for Testing Too** | Can be used in testing setups that are close to real production. |

---


##  Advantages of Gunicorn

- WSGI Compliant – Supports Django, Flask, and other WSGI apps.
- Easy to Use – Simple CLI commands and minimal configuration needed.
- Multi-process Support – Handles concurrent requests via multiple workers.
- Reverse Proxy Compatible – Works well behind Nginx/Apache.

---
##  Disadvantages of Gunicorn

- No Windows Support – Limited or no native support for Windows.
- No Static File Handling – Needs Nginx/Apache to serve static files.
- Not Async by Default – Requires extra config for async support.
- No SSL Handling – Cannot serve HTTPS directly.
- Memory Overhead – Each worker is a separate process, increasing RAM usage.
---

## FAQs

### 1. What is Gunicorn used for?
Gunicorn is a WSGI HTTP server used to run Python web applications like Flask, Django, or FastAPI in production environments.

### 2. Can Gunicorn serve static files?
No, Gunicorn does not serve static files (like images, CSS, or JS). It is recommended to use it behind a reverse proxy like **Nginx** to handle static files and SSL.

### 3. Is Gunicorn asynchronous?
Gunicorn is synchronous by default, but it supports asynchronous workers like **gevent**, **eventlet**, and **gthread** for handling async tasks or long-lived connections.

### 4. Does Gunicorn work on Windows?
Gunicorn is primarily designed for **Unix-like systems** (Linux/macOS) and is not fully supported on Windows.

---

## Contact Information
| Name         | Email address          |
|--------------|------------------------|
| Ishaan         | ishaan.aggarwal.snaatak@mygurukulam.co    |

## References
| Links                                             | Descriptions                                                    |
|---------------------------------------------------|-----------------------------------------------------------------|
| https://docs.gunicorn.org/en/stable/# | Gunicorn Official Site                       |
|  https://medium.com/@serdarilarslan/what-is-gunicorn-5e674fff131b                               | What is Gunicorn |
