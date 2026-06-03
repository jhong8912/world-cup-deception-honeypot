# world-cup-deception-honeypot
World Cup ticketing honeypot and live Kibana security dashboard tracking real-time malicious traffic and bot behavior

# World Cup Ticket Hub: Deception & Logging Honeypot

## 📌 Project Overview
During the 2026 World Cup, cybercriminals heavily target soccer fans using fraudulent ticket resale sites and phishing schemes. To analyze this threat landscape, I engineered a "deception application"—a decoy ticketing platform hosted in the cloud. By intentionally exposing this infrastructure to the public internet, I captured, parsed, and analyzed live global malicious traffic and automated bot behavior in real-time.

* **Core Focus:** Cloud Infrastructure, SIEM & Data Logging, Threat Analysis
* **Tools Used:** AWS (EC2), Linux (Ubuntu), Nginx, Elastic Stack (Elasticsearch, Kibana, Filebeat), Git/GitHub

---

## 🗺️ System Architecture
Below is the data pipeline mapping how an attacker's request is captured and visualized:

[ Attacker/Bot ] ---> [ AWS EC2 / Nginx Web Server ]
│ (Generates access.log)
▼
[ Filebeat Agent ]
│ (Ships data logs)
▼
[ Elasticsearch ] (Ingests & Indexes)
│
▼
[ Kibana Dashboard ] (Visual Analysis)

---

## 🛠️ Implementation Steps

### Phase 1: Cloud Infrastructure & Web Server Setup
* Provisioned an **AWS EC2 (t2.micro)** virtual machine running Ubuntu Linux.
* Configured AWS Security Groups to allow public HTTP traffic (Port 80) and secure SSH management (Port 22).
* Deployed an **Nginx** web server and configured a custom HTML front-end imitating a "World Cup Ticket Resale Hub."

### Phase 2: Log Shipping & SIEM Ingestion
* Installed and configured **Filebeat** on the host server to monitor `/var/log/nginx/access.log`.
* Built an ingestion pipeline to securely ship unstructured web logs directly into a cloud-hosted **Elasticsearch** cluster.

### Phase 3: Kibana Dashboard & Geolocation Data Engineering
* Leveraged Elastic’s GeoIP processor to automatically map raw IP addresses to geographic coordinates.
* Developed a centralized **Kibana Security Dashboard** featuring live attack maps, top targeted URL endpoints, and malicious IP lists.

---

## 📊 Key Security Insights & Findings
*(Note: Update this section at the end of the summer with your actual data!)*
* **Total Attacks Logged:** X,XXX requests over 60 days.
* **Top Origin Countries:** 1. [Country], 2. [Country]
* **Common Attack Paths:** Automated bots frequently attempted directory traversal looking for `/admin`, `/wp-login.php`, and database backup files.

---

## 📁 Repository Structure
* `/src` - Contains the custom HTML/CSS for the decoy World Cup ticketing site.
* `/config` - Contains the anonymized `filebeat.yml` and Nginx server configuration blocks.

---

## 💡 What I Learned
* Hands-on experience navigating and hardening **Linux CLI** environments.
* Practical understanding of **Log Aggregation** and transforming raw data into actionable security metrics.
* Real-world observation of automated threat actor behavior and reconnaissance tactics.
