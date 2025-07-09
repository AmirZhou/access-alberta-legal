# 8. Oracle Cloud APEX Database Always Free Tier

Date: 2025-06-30

## Status

Accepted

## Context

Need cost-effective database solution for legal resources, user data, and location information with room for growth.

## Decision

Use Oracle Cloud Infrastructure Autonomous Database with APEX (Always Free tier):
- **Instance**: AccessAlberaLegalDev (Oracle 23ai)
- **Location**: US San Jose
- **Features**: JSON support, spatial data for GPS, full-text search, AI capabilities
- **Limits**: 20GB storage, 1 ECPU, limited connections
- **Schema**: legal_resources, legal_offices, user_profiles, document_storage

## Consequences

**Positive**: Zero cost, enterprise features, autonomous management, built-in security, APEX admin interfaces
**Negative**: Vendor lock-in, 20GB storage limit, compute constraints, US region latency for Alberta users
**Mitigations**: Monitor usage limits, plan migration path if scaling needed, implement data lifecycle management
