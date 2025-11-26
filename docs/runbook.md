# Runbook

Operational guide for deploying, operating, and maintaining the **Observability Platform with OpenTelemetry**.

## 1. Deployment

### Prerequisites

- AWS CLI configured with appropriate credentials
- Node.js 18+ and npm installed
- AWS CDK CLI installed (`npm install -g aws-cdk`)

### Deploy Steps

```bash
# Install dependencies
npm install

# Bootstrap CDK (first time only)
cdk bootstrap

# Deploy to dev
cdk deploy --context environment=dev

# Deploy to production
cdk deploy --context environment=prod
```

## 2. Scaling

### Horizontal Scaling

- OpenSearch: Add data nodes via CDK context variables
- Lambda collectors: Automatically scales with traffic
- Kinesis: Increase shard count for higher throughput

### Vertical Scaling

- OpenSearch: Upgrade instance types for complex queries
- Lambda: Increase memory allocation for faster processing

## 3. Monitoring

### Key Metrics to Watch

- **Log ingestion rate**: CloudWatch Logs `IncomingBytes`
- **Trace latency**: X-Ray service map latency percentiles
- **OpenSearch health**: Cluster status, JVM memory pressure
- **Lambda errors**: Invocation errors and duration

### Dashboards

Pre-configured CloudWatch dashboards are created during deployment for:

- Service health overview
- Log ingestion metrics
- Trace analytics

## 4. Maintenance

### Regular Tasks

- Review and rotate KMS keys annually
- Update OpenSearch to latest version quarterly
- Review IAM policies for least privilege
- Clean up unused log groups

### Teardown

```bash
cdk destroy --context environment=dev
```

> For troubleshooting common issues, see `docs/troubleshooting.md`.
