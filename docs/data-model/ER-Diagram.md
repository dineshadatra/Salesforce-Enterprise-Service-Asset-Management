# ESAMP — Conceptual Entity Relationship Diagram

**Status:** Approved — Phase 2
**Last Updated:** 2026-08-13

## Overview

This diagram represents the core conceptual data model for ESAMP, based on the
Meridian Field Services business scenario. It shows the primary entities and
their relationships before mapping to specific Salesforce Standard/Custom objects.

## Core Relationships

- **Account** is the central hub — owns Contacts, Assets, Contracts, and submits Cases
- **Asset** connects directly to **Case**, enabling service requests to reference
  the exact piece of equipment involved
- **Case → Service Visit → Inventory Transaction** represents the field service
  fulfillment chain
- **Warehouse → Purchase Order ← Supplier** represents the supply/restocking chain,
  feeding into service fulfillment via Inventory Transactions
- **Case → Invoice → Payment** represents the billing chain triggered by service work

## Notes

- This is a simplified conceptual view. Product/Pricebook, Region, Knowledge, and
  other supporting entities are omitted here for readability and will be
  incorporated as they are built in Phase 3/4.
- Exact cardinalities (one-to-many vs. many-to-many) will be finalized during
  object creation in Phase 3 (Standard Objects) and Phase 4 (Custom Objects).

## Open Architecture Decisions

- **ADR-001 (open):** Supplier — reuse Account with a Record Type, or build a
  custom Supplier__c object? Decision deferred to Phase 4.
- **ADR-002 (open):** Service Contract — use standard Contract, or Field-Service-
  specific ServiceContract? Decision deferred to Phase 3.

## Diagram

See project conversation history / architecture review for the current rendered
ER diagram. (This will be replaced with a static image export once the schema
stabilizes past Phase 4.)