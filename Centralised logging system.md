# Centralized logging system
- Deadline for writing the project proposal is 16th Sep 2022
- Review the sample documents
- Answer the basic questions like: why ? what ? how ? when ? how much ?
- Budget Rs. 5,25,000

# Elastic Stack
## [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/elasticsearch-intro.html)
Search and analytics engine

## Logstash
Server‑side data processing pipeline that ingests data from multiple sources simultaneously, transforms it, and then sends it to a "stash" like Elasticsearch

## Kibana
Visualize data with charts and graphs in Elasticsearch

## [Beats](https://www.elastic.co/guide/en/beats/libbeat/current/beats-reference.html)
Lightweight, single-purpose data shippers that can send data from hundreds or thousands of machines to either Logstash or Elasticsearch.
- [Metricbeats](https://logit.io/sources/configure/metricbeat/)
	Metrics : system and service metrics
- [Filebeat](https://docs.logz.io/shipping/log-sources/filebeat.html)
	Logs: used to send log data
- [Packetbeat](https://www.elastic.co/guide/en/beats/packetbeat/current/packetbeat-overview.html)
	Traces : used to send network data.
	Packetbeat can be installed on the server being monitored or on its own dedicated server
- [Auditbeat](https://www.elastic.co/guide/en/beats/auditbeat/current/auditbeat-overview.html)
	used for auditing user and process activity on your Linux servers.
	can be used to identify security breaches — file changes, configuration changes, malicious behavior.


Generally speaking, there are some basic requirements a production-grade ELK implementation needs to answer:

1.  Save and index all of the log files that it receives (sounds obvious, right?)
2.  Operate when the production system is overloaded or even failing (because that’s when most issues occur)
3.  Keep the log data protected from unauthorized access
4.  Have maintainable approaches to data retention policies, upgrades, and more

### Security
One option is to use nginx reverse proxy to access your Kibana dashboard, which entails a simple nginx configuration that requires those who want to access the dashboard to have a username and password. This quickly blocks access to your Kibana console and allows you to configure authentication as well as add SSL/TLS encryption Elastic

Be careful when exposing Elasticsearch because it is very susceptible to attacks. There are some basic steps to take that will help you secure your Elasticsearch instances.


### Other Links
[Pricing calculator for Elastic Cloud](https://cloud.elastic.co/pricing?baymax=drift&elektra=cloud-pricing)
[Installation on Docker](https://logz.io/blog/elk-stack-on-docker/)


# Alternatives 
- Splunk 
- Microsoft Sentinel
- Helix
- Elastic