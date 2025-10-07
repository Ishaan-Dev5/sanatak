# Middleware Monitoring Dashboard Design Documentation
---
| Author  | Created on | Version   | Last Edited On | Comment  | Reviewer |
|---------|------------|-----------|----------------|-------------------|---------------|
| Shubham | 07-07-25   |  version1| 07-07-25       | Internal Review    |Sahil|
| Shubham | 07-07-25  |  version1|-   | L0  Review  | Gaurav Singla |
| Shubham | 07-07-25  |  version1| -     | L1  Review | Rahul Gupta |
| Shubham | 07-07-25   |  version1| -      | L2  Review  | Mahesh Kumar|

##  Table of Contents
1. [Flow of Designing](#-flow-of-designing)  
2. [Need for Middleware Monitoring](#-need-for-middleware-monitoring)  
3. [Dashboard Design](#-dashboard-design)
4. [Layout](#-layout)
5. [Panels & Visualizations](#-panels--visualizations)  
6. [Alerting and Thresholds](#-alerting-and-thresholds)  
7. [Conclusion & Next Steps](#-conclusion--next-steps)  
7.[ Contact Information](#-contact-information) 

---

##  Flow of Designing
![Untitled-2024-12-14-0039](https://github.com/user-attachments/assets/0cb85f40-f546-4191-bd09-2d2d84879d32)

---
##  Need for Middleware Monitoring
| Purpose                      | Description                                                 |
|-----------------------------|-------------------------------------------------------------|
| **Performance Tracking**     | Monitor queue depths, response time, and throughput.        |
| **Error Visibility**         | Detect message failures, dead-letter queues, timeouts.      |
| **Capacity Planning**        | Evaluate trends in memory, CPU usage, and queue growth.     |
| **Alerting & Automation**    | Trigger alerts for unusual spikes or downtimes.             |
| **Business Reliability**     | Ensure smooth flow between decoupled components.            |

---

##  Dashboard Design
<img width="3173" height="1383" alt="redis-dasshboard" src="https://github.com/user-attachments/assets/5c102c5d-7248-44fc-93d4-d42fcf0238e9" />

###  Layout
| Region               | Span       | Purpose                                              |
|-------------------------|--------------|-----------------------------------------------------------|
| Top Banner              | Full width   | Dashboard title, time range selector, environment tag     |
| Row 1: Health KPIs      | 3 columns    | Uptime, Ops/sec, Cache Hit Ratio                          |
| Row 2: Memory & Clients | 2/3 width    | Used memory, connected clients, blocked clients           |
| Row 2: CPU & Disk       | 1/3 width    | CPU usage, Redis process CPU, system CPU, disk I/O        |
| Row 3: Persistence      | Full width   | AOF/RDB save/write status, with stat indicators           |
| Row 4: Replication      | 1/2 width    | Replication lag, replica sync status                      |
| Row 4: Restarts         | 1/2 width    | Uptime in seconds, restarts over time                     |

---

###  Panels & Visualizations
### 1. **Memory Usage**
- **Metric**: `redis_memory_used_bytes`
- **Panel**: Gauge (thresholds at 75%, 85%)
- **Source**: Redis Exporter → Prometheus
### 2. **Connected Clients**
- **Metric**: `redis_connected_clients`
- **Panel**: Stat
- **Note**: Compare with `maxclients`
### 3. **Ops per Second**
- **Metric**: `rate(redis_commands_processed_total[1m])`
- **Panel**: Time series line chart
### 4. **Cache Hit Ratio**
- **Metric**: `(hits / (hits + misses)) * 100`
- **Panel**: Stat (green if >90%)
### 5. **Blocked Clients**
- **Metric**: `redis_blocked_clients`
- **Panel**: Stat or trend over time
### 6. **CPU Usage**
- **Metric**: `rate(redis_cpu_sys_seconds_total[1m]) + rate(redis_cpu_user_seconds_total[1m])`
- **Panel**: Line chart or stacked area
### 7. **AOF & RDB Status**
- **Metric**: `redis_aof_last_write_status`, `redis_rdb_last_bgsave_status`
- **Panel**: Single stat (mapped "1" → OK, "0" → Failed)
### 8. **Replication Lag**
- **Metric**: `redis_replication_master_last_io_seconds_ago`
- **Panel**: Stat
### 9. **Uptime & Restart Tracking**
- **Metric**: `redis_uptime_in_seconds`
- **Panel**: Stat + graph (to detect restarts)
### 10. **Redis Logs**
- **Source**: Loki / Elasticsearch / CloudWatch Logs
- **Panel**: Table with severity, timestamp, and message

---

##  Alerting and Thresholds
| Alert Name           | Condition                              | Severity | Action                    |
|----------------------|----------------------------------------|----------|----------------------------|
| High Queue Depth     | queue depth > 10,000 for 5 mins         | Critical | Page team via PagerDuty   |
| Message Failure Rate | failure rate > 2%                      | Warning  | Slack alert                |
| Host Resource Usage  | CPU > 85% or Memory > 90%              | Warning  | Auto-scale or investigate  |
| No Metrics Detected  | No data for middleware exporter > 1m   | Critical | Restart agent / alert     |

---

##  Conclusion & Next Steps
- Deploy the dashboard to staging and production environments.
- Review alerts and test conditions.
- Integrate notification channels (Slack, OpsGenie, Email).
- Continuously iterate based on middleware growth and feedback.
---

###  Contact Information
| Name | Email Address |
|------|---------------|
| Shubham Prasad | [shubham.prasad.snaatak@mygurukulam.co](mailto:shubham.prasad.snaatak@mygurukulam.co) |
