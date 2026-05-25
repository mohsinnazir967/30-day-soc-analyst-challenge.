# 🔌 Elastic Stack Default Port Reference

Quick reference for all default ports used in the ELK Stack — essential for firewall rules and cloud security group configuration during lab setup.

---

## Port Reference Table

| Service | Default Port | Protocol | Notes |
|---------|-------------|----------|-------|
| Elasticsearch HTTP | `9200` | TCP | REST API — used by Kibana and Elastic Agent |
| Elasticsearch Transport | `9300` | TCP | Inter-node cluster communication |
| Kibana | `5601` | TCP | Web UI — access via browser |
| Logstash Beats Input | `5044` | TCP | Receives logs from Beats/Elastic Agent |
| Logstash HTTP | `9600` | TCP | Logstash monitoring API |
| Fleet Server | `8220` | TCP | Elastic Agent enrollment and management |
| Elastic Agent (metrics) | `8200` | TCP | APM Server default |
| Elastic Defend | `443` | TCP | Communicates over standard HTTPS |

---

## Cloud Firewall Rules Needed

When setting up on Vultr (or any cloud provider), open these ports on your ELK server:

```
Inbound:
- TCP 9200   → Elasticsearch API (restrict to your IP only)
- TCP 5601   → Kibana UI (restrict to your IP only)
- TCP 8220   → Fleet Server (allow from agent machines)
- TCP 5044   → Logstash input (allow from agent machines)

Outbound:
- All traffic allowed
```

> ⚠️ **Security tip:** Never expose port 9200 (Elasticsearch) to the public internet. Always restrict to known IPs or use a VPN.

---

## Quick Health Checks

```bash
# Check Elasticsearch is running
curl -X GET "localhost:9200"

# Check Kibana is running
curl -X GET "localhost:5601/api/status"

# Check Fleet Server status
curl -X GET "localhost:8220/api/status"
```

---

*Reference used throughout the [30-Day SOC Analyst Challenge](../README.md)*
