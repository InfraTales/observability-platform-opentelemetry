# Cost Analysis (₹)

This document provides cost estimates for the **Observability Platform with OpenTelemetry** architecture in **Indian Rupees (₹)**.

## Production Environment

At production scale (100+ microservices, multi-region), the architecture typically costs:

| Service | Monthly Cost (₹) | Notes |
|---------|------------------|-------|
| **CloudWatch Logs** | ₹15,000–25,000 | Log ingestion and storage |
| **X-Ray** | ₹8,000–12,000 | Distributed tracing |
| **OpenSearch** | ₹40,000–60,000 | Log analytics and dashboards |
| **Lambda (collectors)** | ₹5,000–10,000 | OTEL collector functions |
| **Kinesis Firehose** | ₹8,000–15,000 | Log streaming |
| **S3 (archives)** | ₹3,000–5,000 | Long-term log storage |
| **Total** | **₹80,000–130,000** | ~$1,000–1,600/month |

## Development Environment

For dev/staging (fewer services, lower retention):

| Environment | Approx Monthly Cost (₹) | Notes |
|------------|--------------------------|-------|
| Dev | ₹15,000–25,000 | Single region, reduced retention |
| Staging | ₹30,000–50,000 | Multi-region, moderate scale |
| Production | ₹80,000–130,000 | Full scale, 100+ services |

## Cost Optimization Strategies

- **Log sampling** – Sample verbose logs at high traffic to reduce ingestion costs
- **Tiered storage** – Move older logs to S3 Glacier for long-term retention
- **Metric aggregation** – Pre-aggregate metrics before sending to CloudWatch
- **Right-size OpenSearch** – Use reserved instances for predictable workloads
- **Trace sampling** – Sample traces at 10-20% for high-traffic services

## Related Documentation

See the project README for architecture details.md` for environment-specific configurations.
