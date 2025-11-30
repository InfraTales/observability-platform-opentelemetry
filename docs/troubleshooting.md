# Troubleshooting

Common issues and resolutions for the **Observability Platform with OpenTelemetry**.

## Deployment Issues

### 1. CDK Bootstrap Fails

**Symptom:** `cdk bootstrap` fails with permission errors.

**Resolution:**
- Verify AWS credentials have `cloudformation:*` and `s3:*` permissions
- Check the target account and region are correct

### 2. OpenSearch Cluster Creation Timeout

**Symptom:** Stack creation times out waiting for OpenSearch.

**Resolution:**
- OpenSearch clusters can take 15-30 minutes to create
- Increase CDK timeout or check AWS console for cluster status
- Verify VPC subnet configuration has available IPs

## Data Ingestion Issues

### 3. Logs Not Appearing in OpenSearch

**Symptom:** Services are sending logs but they don't appear in dashboards.

**Resolution:**
- Check Kinesis Firehose delivery errors in CloudWatch
- Verify Lambda collector IAM permissions
- Check OpenSearch index patterns match incoming data

### 4. High Trace Latency

**Symptom:** X-Ray traces show unusually high latency.

**Resolution:**
- Check Lambda cold starts – enable provisioned concurrency
- Review OTEL collector batch settings
- Verify network path between services and X-Ray endpoint

## Performance Issues

### 5. OpenSearch Slow Queries

**Symptom:** Dashboard queries take too long.

**Resolution:**
- Check JVM memory pressure – scale up instance type
- Review index mapping for inefficient field types
- Enable slow query logging to identify problematic queries

### 6. Lambda Collector Throttling

**Symptom:** Collector functions hitting concurrency limits.

**Resolution:**
- Request concurrency limit increase via AWS Support
- Implement buffering in application instrumentation
- Consider dedicated collector deployment (ECS/EKS)

## Cost Issues

### 7. Unexpected High Costs

**Symptom:** Monthly bill higher than estimates.

**Resolution:**
- Review CloudWatch Logs ingestion – check for verbose logging
- Check OpenSearch storage – implement lifecycle policies
- Enable log sampling for high-traffic services

> For architecture details, see the project README.
