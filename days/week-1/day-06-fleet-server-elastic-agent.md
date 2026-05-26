# Day 06: Understanding Fleet Server and Elastic Agent

**Week:** 1 | **Phase:** Agent Management Theory
**← [Back to README](../../README.md) | [← Day 05](./day-05-windows-server-cloud.md)**

---

## 1. Introduction

**Scenario:** Managing 100 Windows machines with Elastic Agent.

**Options:** Manually configure each agent, use group policy, or utilize a Fleet Server for centralized management.

---

## 2. Elastic Agent

- **Function:** Unified monitoring for logs, metrics, and other data.
- **Policies:** Update and add integrations to control log forwarding to Elasticsearch or Logstash.
- **Installation Methods:** Standalone or Fleet-managed.

---

## 3. Beats vs Elastic Agent

| Feature | Beats | Elastic Agent |
|---------|-------|---------------|
| Agents needed | Six types, may require multiple on a single host | Single agent for various logs |
| Management | Manual per-agent | Centralized via Fleet |
| Use case | Specialized per log type | Sufficient for most use cases |

Reference: [Beats vs Elastic Agent Comparison](https://www.elastic.co/guide/en/fleet/current/beats-agent-comparison.html#additional-capabilities-beats-and-agent)

---

## 4. Fleet Server

- **Function:** Connects Elastic Agents to a Fleet for centralized management.
- **Benefits:** Easy policy updates, new integrations, data forwarding, agent updates, and enrollment.
- **Without Fleet Server:** Manual updates are required, which can be difficult at scale.

---

*→ Next: [Day 07 — Fleet Server Setup](./day-07-fleet-server-setup.md)*
