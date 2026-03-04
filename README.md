# ELK-Stack-Deployment-for-Monitoring1

Project Overview

This project demonstrates how to deploy the ELK Stack (Elasticsearch, Logstash, and Kibana) to monitor system and application logs.

The ELK stack collects logs from applications or servers, processes them using Logstash, stores them in Elasticsearch, and visualizes them through Kibana dashboards.

This solution helps teams monitor infrastructure, troubleshoot issues, and analyze application logs in real time.

Technologies Used

Elasticsearch

Logstash

Kibana

Linux

AWS EC2

ELK Stack Architecture:-
Application Logs / System Logs
            │
            ▼
        Logstash
     (Log Processing)
            │
            ▼
      Elasticsearch
      (Data Storage)
            │
            ▼
          Kibana
   (Visualization Dashboard)

 Components of ELK Stack
Elasticsearch

Distributed search and analytics engine

Stores logs and indexed data

Logstash

Data processing pipeline

Collects and transforms logs

Kibana

Visualization tool

Creates dashboards and graphs from Elasticsearch data

Step 1: Launch EC2 Instance


Create an EC2 instance with:

OS: Amazon Linux / Ubuntu

Instance type: t2.micro

Open required ports:

Service	Port
SSH	22
Elasticsearch	9200
Kibana	5601


Step 2: Install Java

ELK stack requires Java.

sudo yum install java-17-amazon-corretto -y

Verify installation:

java -version


Step 3: Install Elasticsearch

Download and install Elasticsearch.

Start service:

sudo systemctl start elasticsearch

Enable service:

sudo systemctl enable elasticsearch

Verify:

curl localhost:9200


Step 4: Install Logstash

Install Logstash and configure it to process logs.

Example pipeline configuration:

input {
  file {
    path => "/var/log/messages"
  }
}

output {
  elasticsearch {
    hosts => ["localhost:9200"]
  }
}


Step 5: Install Kibana

Start Kibana service:

sudo systemctl start kibana

Enable service:

sudo systemctl enable kibana


Step 6: Access Kibana Dashboard

Open browser:

http://EC2-Public-IP:5601


Kibana UI will appear where logs can be visualized.



