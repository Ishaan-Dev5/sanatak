# Gunicorn (Green Unicorn) Documentation

---

### Author Information

| Author      | Created on  | Version    |   Last updated on | Internal Reviewer | L0 Reviewer  | L1 Reviewer | L2 Reviewer      |
|-------------|-------------|------------|-----------------|----------------|-------------------|---------------|----------------------------------|
| Ishaan    | 20-07-25    | v1.0  |       20-07-25       | Rohit Chopra    |  Akshit/Nitik    | Taran        | Abhishek Dubey/ Rishab sharma |

## Table of Contents 

1. [Introduction](#1-introduction)
2. [What is gunicorn](#2-what-is-gunicorn)
3. [Why We need Gunicorn](#3-why-we-need-gunicorn)
4. [Features](#4-Features-Of-Gunicorn)
5. [Use Cases](#5-use-cases-of-gunicorn)
6. [Advantages of Gunicorn](#6-advantages-of-gunicorn)
7. [Disadvantages of Gunicorn](#7-Disadvantages-of-gunicorn)
8. [Conclusion](#8-Conclusion)
9. [FAQs](#9-FAQs)
10. [Contact Information](#10-contact-information)
11. [References](#11-references)

---

## 1. Introduction

This document provides a structured overview of Gunicorn (Green Unicorn) — a WSGI-compliant HTTP server for running Python web applications. It explains what Gunicorn is, why it is needed, its core features.

---

## 2. What is gunicorn
Gunicorn (Green Unicorn) is a WSGI-compliant HTTP server for Python web applications. It receives client requests via a web server (like Nginx) and forwards them to Python applications built with WSGI-compatible frameworks such as Flask, Django, or FastAPI.
Gunicorn is one implementation of a WSGI server for Python applications.

---

## 3. Why we need gunicorn?

The standard web servers such as Apache, and NGINX don’t know how to communicate with your Python applications. Web servers receive the request from a client(Web browser) and return a response. The web server doesn’t create the response, it only returns the response. So, a server needs to talk with a Web Application that can create a response.

Python web applications need an interface to connect with web servers — this is where WSGI (Web Server Gateway Interface) comes in.

WSGI  basically provides that bridge of your need to communicate between your Web Server and Web Application. WSGI (Web Server Gateway Interface), is a set of rules which allow a WSGI compliant server to work with a WSGI compliant Python application. WSGI also handles scaling for web servers to be able to handle thousands of requests so you don’t have to think about accepting multiple requests at a time.


<img width="1534" height="425" alt="image" src="https://github.com/user-attachments/assets/2a7b0f1c-0585-4346-afe5-8cb793c45248" />



### Deplyoment Before GUnicorn

Before the widespread use of Gunicorn, Python web applications were often deployed using a variety of methods, including: Flask's built-in development server (which is not suitable for production), other WSGI servers like Waitress or uWSGI, or directly through web servers like Apache or Nginx with a WSGI module

---


## 4. Features of Gunicorn

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


##  5. Use Cases of Gunicorn

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


##  6. Advantages of Gunicorn

| Feature                  | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| WSGI Compliant           | Supports Django, Flask, and other WSGI apps.                               |
| Easy to Use              | Simple CLI commands and minimal configuration needed.                      |
| Multi-process Support    | Handles concurrent requests via multiple workers.                          |
| Reverse Proxy Compatible | Works well behind Nginx/Apache.                                            |

---
##  7. Disadvantages of Gunicorn

| Limitation               | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| No Windows Support       | Limited or no native support for Windows.                                  |
| No Static File Handling  | Needs Nginx/Apache to serve static files.                                  |
| Not Async by Default     | Requires extra config for async support.                                   |
| No SSL Handling          | Cannot serve HTTPS directly.                                               |
| Memory Overhead          | Each worker is a separate process, increasing RAM usage.                   |

---

## 8. Conclusion

Gunicorn is a powerful, lightweight, and production-ready WSGI server designed to run Python web applications efficiently. Its multi-process architecture, easy configuration, and compatibility with popular frameworks make it a preferred choice for deploying apps behind web servers like Nginx. While it requires external support for static file handling, SSL, and Windows compatibility, Gunicorn remains a widely adopted solution in both cloud-native and containerized environments.

---

## 9. FAQs

### 1. What is Gunicorn used for?
Gunicorn is a WSGI HTTP server used to run Python web applications like Flask, Django, or FastAPI in production environments.

### 2. Can Gunicorn serve static files?
No, Gunicorn does not serve static files (like images, CSS, or JS). It is recommended to use it behind a reverse proxy like **Nginx** to handle static files and SSL.

### 3. Is Gunicorn asynchronous?
Gunicorn is synchronous by default, but it supports asynchronous workers like **gevent**, **eventlet**, and **gthread** for handling async tasks or long-lived connections.

### 4. Does Gunicorn work on Windows?
Gunicorn is primarily designed for **Unix-like systems** (Linux/macOS) and is not fully supported on Windows.

---

## 10. Contact Information
| Name         | Email address          |
|--------------|------------------------|
| Ishaan         | ishaan.aggarwal.snaatak@mygurukulam.co    |

---

## 11. References
| Links                                             | Descriptions                                                    |
|---------------------------------------------------|-----------------------------------------------------------------|
| Gunicorn Official Site    | [Visit](https://docs.gunicorn.org/en/stable/#)                     |
 | What is Gunicorn |  [Visit](https://medium.com/@serdarilarslan/what-is-gunicorn-5e674fff131b)                              |

