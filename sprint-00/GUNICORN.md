
<img width="300" height="250" alt="images (1)" src="https://github.com/user-attachments/assets/132f42a1-8fa1-4298-990b-16088a091c93" />



# Gunicorn (Green Unicorn) Documentation

---

### Author Information

| **Author**   | **Created on** | **Version** | **Last updated by** | **Last edited on** | **Level** | **Reviewer**  |
|--------------|----------------|-------------|---------------------|--------------------|-----------|---------------|
| Ishaan    | 20-07-25    | v1.0  |  Ishaan  |20-07-25   | Internal    | Rohit Chopra    | 

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

WSGI  basically provides that bridge of your need to communicate between your Web Server and Web Application. WSGI (Web Server Gateway Interface), is a set of rules which allow a WSGI compliant server to work with a WSGI compliant Python application. WSGI also handles scaling for web servers to be able to handle thousands of requests.


<img width="1534" height="425" alt="image" src="https://github.com/user-attachments/assets/2a7b0f1c-0585-4346-afe5-8cb793c45248" />



#### Deplyoment Before GUnicorn

Before the widespread use of Gunicorn, Python web applications were often deployed using a variety of methods, including: Flask's built-in development server (which is not suitable for production), other WSGI servers like Waitress or uWSGI, or directly through web servers like Apache or Nginx with a WSGI module

---


## 4. Features of Gunicorn

|  Feature                  |  Description |
|----------------------------|----------------|
| **WSGI Compliance**        | Works well with Python web frameworks like Django, Flask, and FastAPI. |
| **Supports Sync & Async**  | Can handle both traditional and simultaneous tasks |
| **Lightweight & Fast**     | Runs quickly and doesn't use too many system resources. |
| **Automatic Worker Management** | Automatically restarts or replaces stuck or slow workers. |
| **Framework Agnostic**     | Can be used with any Python web framework that follows WSGI. |


---


##  5. Use Cases of Gunicorn

|  Use Case |  Description |
|-------------|----------------|
| **Run Python Web Apps** | Helps run Python websites made with Flask, Django |
| **For Live/Production Use** | Can handle real users and traffic, good for live websites. |
| **Works with Nginx/Apache** | Often used behind Nginx or Apache, which handles static files and SSL. |
| **Used in Docker/Kubernetes** | Works well inside containers and cloud platforms for microservices. |
| **Simpler than uWSGI** | Easier to set up than uWSGI but does a similar job. |


---


##  6. Advantages of Gunicorn

| Feature                  | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| **WSGI Compliant**           | Supports Django, Flask, and other WSGI apps.                               |
| **Easy to Use**              | Simple CLI commands and minimal configuration needed.                      |
| **Multi-process Support**    | Handles concurrent requests via multiple workers.                          |
| **Reverse Proxy Compatible** | Works well behind Nginx/Apache.                                            |

---

##  7. Disadvantages of Gunicorn

| Limitation               | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| **No Windows Support**       | Limited or no native support for Windows.                                  |
| **No Static File Handling**  | Needs Nginx/Apache to serve static files.                                  |
| **Not Async by Default**     | Requires extra config for async support.                                   |
| **No SSL Handling**          | Cannot serve HTTPS directly.                                               |

---

## 8. Conclusion

Gunicorn is a powerful, lightweight, and production-ready WSGI server designed to run Python web applications efficiently. Its multi-process architecture, easy configuration, and compatibility with popular frameworks make it a preferred choice for deploying apps behind web servers like Nginx. While it requires external support for static file handling, SSL, and Windows compatibility, Gunicorn remains a widely adopted solution in both cloud-native and containerized environments.

---

## 9. FAQs

#### 1. What is Gunicorn used for?
Gunicorn is a WSGI HTTP server used to run Python web applications like Flask, Django, or FastAPI in production environments.

#### 2. Can Gunicorn serve static files?
No, Gunicorn does not serve static files (like images, CSS, or JS). It is recommended to use it behind a reverse proxy like **Nginx** to handle static files and SSL.

#### 3. Is Gunicorn asynchronous?
Gunicorn is synchronous by default, but it supports asynchronous workers like **gevent**, **eventlet**, and **gthread** for handling async tasks or long-lived connections.

#### 4. Does Gunicorn work on Windows?
Gunicorn is primarily designed for **Unix-like systems** (Linux/macOS) and is not fully supported on Windows.

---

## 10. Contact Information

| Name| Email Address      | GitHub | URL |
|-----|--------------------------|----------|---------|
| Ishaan | ishaan.aggarwal.snaatak@mygurukulam.co|  Ishaan-Dev1  | https://github.com/Ishaan-Dev1  |

---

## 11. References
| Title                                            | Links                                                 |
|---------------------------------------------------|-----------------------------------------------------------------|
| Gunicorn Official Site    | [Visit](https://docs.gunicorn.org/en/stable/#)                     |
 | What is Gunicorn?|  [Visit](https://medium.com/@serdarilarslan/what-is-gunicorn-5e674fff131b)                              |

