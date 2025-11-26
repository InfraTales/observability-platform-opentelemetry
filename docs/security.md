# Security Overview

This document summarizes the security posture of the **Observability Platform with OpenTelemetry** architecture.

## Defense-in-Depth

The system applies multiple layers of security controls:

### Identity & Access (IAM)

- Least-privilege IAM roles for all Lambda functions and collectors
- Separate roles for log ingestion, processing, and querying
- Service-linked roles for OpenSearch and CloudWatch

### Network Isolation

- VPC deployment for OpenSearch clusters
- Private subnets for data processing components
- Security groups restricting access to required ports only
- VPC endpoints for AWS service access

### Encryption

- **At rest**: KMS encryption for CloudWatch Logs, OpenSearch, S3 archives
- **In transit**: TLS 1.2+ for all service-to-service communication
- Customer-managed KMS keys for sensitive environments

### Data Protection

- PII scrubbing in log pipelines before storage
- Log retention policies aligned with compliance requirements
- Access logging for audit trails

## Observability Security

- CloudTrail integration for API audit logs
- Anomaly detection on log access patterns
- Alerting on unauthorized access attempts

## Compliance Considerations

The architecture supports:

- SOC 2 Type II controls
- GDPR data protection requirements
- HIPAA logging requirements (with appropriate configuration)

> For detailed security configurations, see `SECURITY.md` in the project root.
