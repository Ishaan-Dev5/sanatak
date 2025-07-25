| Author      | Created on  | Version    | Last updated by | Last edited on |
|-------------|-------------|------------|-----------------|----------------|
| ABC    | 10-08-23    | version 1  | ABC        | 24-08-23       |

## Purpose
Explain the purpose of this application. Why there was a need for this application and what problems does it solve. 

## Pre-requisites
Before diving into application deployment, let’s ensure the following Hardware, Software and Security requirements are met.

## System Requirements
| Hardware Specifications | Minimum Recommendation |
|--------------------------|------------------------|
| Processor                | dual-core              |
| RAM                      | 4GB                    |
| Disk                     | 20GB                   |
| OS                       | Ubuntu(22.04)          |

## Dependencies
### Build time Dependency
| Name           | Version | Description        |
|----------------|---------|--------------------|
| `<application>` | `<version>` | `<Description>` |
| `<application>` | `<version>` | `<Description>` |

###  Run time Dependency
| Name           | Version    | Description        |
| -------------- | ---------- | ------------------ |
| `<application>` | `<version>`| `<Description>`   |
| `<application>` | `<version>`| `<Description>`   |

### Other Dependency
| Name           | Version    | Description        |
| -------------- | ---------- | ------------------ |
| `<application>` | `<version>`| `<Description>`   |
| `<application>` | `<version>`| `<Description>`   |

## Important Ports
| Inbound Traffic | Description        |
| --------------- | ------------------ |
| 9042            | Used by ScyllaDB   |

| Outbound Traffic | Description           |
| ---------------- | --------------------- |
| 8080             | Used by Tomcat-server |

## Others
| Others                  | Description               |
| ----------------------- | ------------------------- |
| Additional requirements | Description               |

## Architecture
![image](https://github.com/OT-MICROSERVICES/documentation-template/assets/135941107/489b8e01-0027-452a-9b5f-92ea7cd2734e)

## Dataflow Diagram
Explain the flow of the data in this diagram. How the data is traveling/flowing in this application.

## Step-by-step installation of [application]
### Step1: Installation of software Dependencies

#### Build Dependency
Add the command used to install the dependency in code snippet format. 
[command]
#### Run time Dependency
Add the command used to install the dependency in code snippet format. 
[command]
#### Other Dependency
These are the dependencies specific to integration of your application with 3rd party application.

### Step2: Build/Artifact Generation
* Clone the git repository
  [commands]   
* Run the following command inside the directory to build your software artifact.
  [commands]   

### Step3: Application Deployment
* Perform the following steps to deploy the software artifact.
  [command]
* Ensure the application deployed is in working state
  [command]

## Monitoring
Monitoring in DevOps refers to the practice of continuously observing and collecting data from various components of an application or system to ensure its health, performance, and availability. It involves tracking various metrics, events, and logs to identify issues, anomalies, and opportunities for improvement. Monitoring is a crucial aspect of the DevOps lifecycle as it helps teams proactively manage and maintain their applications, enabling faster response to problems and better overall system performance.

#### Metrics
| Parameter           | Description                                                | Priority | Threshold          |
|---------------------|------------------------------------------------------------|----------|--------------------|
| Disk Utilization    | The percentage of disk space used by the application.      | High     | >90%               |
| Availability        | The percentage of time the application is available.        | High     | >= 99.9%           |
| Memory Utilization  | The percentage of memory used by the application.           | Medium   | >80%               |
| CPU Utilization     | The percentage of CPU time used by the application.         | Medium   | >70%               |
| Network Traffic     | The amount of network traffic generated by the application. | Medium   | Varies based on use case |
| Latency             | The time taken for the application to respond to a request. | High     | < 300ms            |
| Errors              | The number of errors generated by the application.          | High     | > 5 per minute     |
| Throughput          | The number of requests the application can handle per unit of time. | High | > 1000 requests per minute |
| Security            | The security of the application (authentication, authorization, encryption). | High | Continuous monitoring |
#### Health check
| Name     | Type           | InitialDelaySeconds | PeriodSeconds | TimeoutSeconds | SuccessThreshold | FailureThreshold |
|----------|----------------|---------------------|---------------|-----------------|-------------------|-------------------|
| App name | ReadinessProbe  | 10                  | 10            | 5               | 1                 | 3                 |
| App name | LivenessProbe   | 10                  | 10            | -               | 5                 | 1
#### Explanation of parameters used in above table
| Parameter             | Description                                                    |
|-----------------------|----------------------------------------------------------------|
| ReadinessProbe        | This probe checks if the application is ready to receive traffic. |
| LivenessProbe         | This probe checks if the application is still running and responding to requests. |
| InitialDelaySeconds   | The number of seconds to wait before the first health check is performed. |
| PeriodSeconds         | The frequency at which the health check should be performed.    |
| TimeoutSeconds        | The maximum amount of time that the health check should wait for a response before it considers the application unhealthy. |
| SuccessThreshold      | The number of consecutive successful health checks before the application is considered healthy. |
| FailureThreshold      | The number of consecutive unhealthy health checks before the application is considered unhealthy. |

## Logging
This offers all types of logs related to the application like: Event Logs, Server Logs, System Logs, Authorization and Access Logs, Change Logs, Availability Logs, Resource Logs, Threat Logs
| Event Logs     | Description                                                                                             |
|----------------|---------------------------------------------------------------------------------------------------------|
|     `location/to/event.log`           | An event log is a high-level log that records network traffic and usage data such as incorrect password attempts, login attempts, and application events. |

| Authentication & Authorization Logs | Description |                                                                                       
|--------------------------------------|---------------------------------------------------------------------------------------------------|
|           `location/to/access.log`   | Authorization and access logs contain a list of persons or bots who have accessed specific programs or files. |

| Server Logs | Description                                                              |
|-------------|--------------------------------------------------------------------------|
| `location/to/server.log`  | A server log is a text document that keeps track of actions on a certain server over some time. |

| Threat Logs | Description                                                                      |
|-------------|----------------------------------------------------------------------------------|
| `location/to/threat.log` | Threat logs are logs that contain information on the system, file, or application traffic that matches a firewall's security profile. |

## Disaster Recovery
In the event of a disaster affecting the application's functionality, it's important to have a robust disaster recovery plan in place. It typically ensures that critical systems and data can be restored after a disaster.

Disaster could be caused by a natural disaster, a cyberattack, or other event that takes down your IT infrastructure.

## High Availability
Ensuring high availability of the application is crucial to minimize downtime and provide seamless service to users. High Availability is a design approach that minimizes downtime for critical systems and services. This is achieved by deploying redundant components and systems, so that if one component fails, another can take over.

Note: In other words, DR is focused on recovering from a disaster, while HA is focused on preventing downtime.

## Troubleshooting
Mention all the common issues that you encountered while performing setup of the Application. If you think there are some specific errors that are seen, you can add their screenshots or give a brief explanation of issue and offer solution to resolve it or guide the user to troubleshoot easily.

## FAQs
- **Is this application free?**
  - Yes, it is an open-source application.

- **Can I deploy this application on all Cloud platforms?**
  - Yes, it can be deployed on any cloud platform.

- **Do you offer an enterprise version of this application?**
  - No, this is open-source contribution. No enterprise version available.

## Contact Information
| Name         | Email address          |
|--------------|------------------------|
| abc          | abc@mygurukulam.co     |

## References
| Links                                             | Descriptions                                                    |
|---------------------------------------------------|-----------------------------------------------------------------|
| [https://www.jenkins.io/doc/book/installing/linux/#debianubuntu](https://www.jenkins.io/doc/book/installing/linux/#debianubuntu) | Document format followed from this link                         |
| [https://amplifi.com/user-guide/FAQs.html](https://amplifi.com/user-guide/FAQs.html)                                     | Documentation referred for the table of contents to be included |
| [https://thecontentauthority.com/blog/introduction-vs-overview](https://thecontentauthority.com/blog/introduction-vs-overview) | This link explains the difference between Overview & Intro      |
 















 