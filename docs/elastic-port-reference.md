# 🔌 Elastic Stack Default Port Reference

Quick reference for all default ports used in the ELK Stack — essential for firewall rules and cloud security group configuration during lab setup.

---

## Port Reference Table

| Component Communication | Default Port |
|-------------------------|-------------|
| Elastic Agent → Fleet Server | `8220` |
| Elastic Agent → Elasticsearch | `9200` |
| Elastic Agent → Logstash | `5044` |
| Elastic Agent → Kibana (Fleet) | `5601` |
| Fleet Server → Kibana (Fleet) | `5601` |
| Fleet Server → Elasticsearch | `9200` |

---

## Cloud Firewall Rules Needed

When setting up on Vultr, open these ports on your ELK server:

```
Inbound:
- TCP 9200   → Elasticsearch API     (restrict to your IP only)
- TCP 5601   → Kibana UI             (restrict to your IP only)
- TCP 8220   → Fleet Server          (allow from agent machines)
- TCP 5044   → Logstash input        (allow from agent machines)

Outbound:
- All traffic allowed
```

> ⚠️ **Security Tip:** Never expose port `9200` (Elasticsearch) to the public internet. Always restrict to known IPs or use a VPN.

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
