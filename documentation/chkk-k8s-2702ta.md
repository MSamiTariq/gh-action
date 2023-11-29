---
title: CockroachDB crashes when performing range scan against a virtual table that has a virtual index
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade CockroachDB to version 20.2.3 or newer. See CockroachDB's [documentation for cluster upgrades](https://www.cockroachlabs.com/docs/stable/upgrade-cockroachdb-kubernetes.html).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation available for this ARSig.

## What is the impact? (Availability Impact)

This causes downtime if traffic is sent to the crashed pod.

## Why does this exist? (Root Cause)

The database would panic when a user performed a range scan against a virtual table[1] that had a virtual index[2]. For example, a query such as

```sql
SELECT * FROM pg_catalog.pg_type WHERE oid IN (19, 20)
```

would trigger this crash, if the table has a virtual index defined on its `oid` columns. This defect occurs in the code when the virtual table span is truncated according to the specified index constraints. This has been fixed in CockroachDB versions >= v20.2.3

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using CockroachDB versions `v20.2.0`, `v20.2.1` and `v20.2.2` contain this Latent Availability Risk.

## Additional Resources

For more information see:

- [Bug Fixes introduced in CockroachDB v20.2.3 release](https://www.cockroachlabs.com/docs/releases/v20.2#v20-2-3-bug-fixes)
- [The original GitHub issue](https://github.com/cockroachdb/cockroach/issues/56440)
- [The PR that fixed this issue](https://github.com/cockroachdb/cockroach/pull/56924)
- [Documentation for CockroachDB's cluster upgrades](https://www.cockroachlabs.com/docs/stable/upgrade-cockroachdb-kubernetes.html)

<br/>

[1] Virtual tables are a special version of tables in SQL. They provide an environment for various complex operations. You can select data from multiple tables, or you can select specific data based on certain criteria in views. It does not hold the actual data; it holds only the definition of the view in a data dictionary.

[2] Virtual indexes are used to simulate the existence of an index and test its impact without actually building the actual index.