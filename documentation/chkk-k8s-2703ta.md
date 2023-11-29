---
title: In CockroachDB v23.1.0 inserting rows into a multi-column-family table with COPY can corrupt the table.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your CockroachDB version to `v23.1.1` or greater.

## How to fix it, short-term workaround? (Mitigation)

This defect can be mitigated by setting the [session variable](https://www.cockroachlabs.com/docs/v23.1/set-vars) `vectorize` to `off`, or setting `copy_fast_path_enabled` to `off` in any session that executes the `COPY` command.

## What is the impact? (Availability Impact)

In CockroachDB `v23.1.0` and its testing versions, executing `COPY` into a target table that has multiple [column families](https://www.cockroachlabs.com/docs/v23.1/column-families) can corrupt the table. Future reads on the corrupted table can result in internal errors or silent data corruption. If data was copied into a table with existing rows, the data in those rows may be irrecoverable.

## Why does this exist? (Root Cause)

The issue occurred when handling batches of key-value pairs (KV batches) that were sorted before being handed off to the KV layer. When multiple groups of columns (column families) were in use, the sorting would mix up the keys and make it invalid to reuse them for prefix keys across families.

Due to the severity of the issue, CockroachDB has withdrawn the `v23.1.0` release and removed the links to the downloads and Docker image.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using CockroachDB versions lesser than `v23.1.1` contain this Latent Availability Risk.

## Additional Resources

For more information, please refer to 

1. [v23.1.0 Release Notes](https://www.cockroachlabs.com/docs/releases/v23.1.html#v23-1-0)
2. [Official Technical Advisory](https://www.cockroachlabs.com/docs/advisories/a103220)
3. [PR that fixed this issue](https://github.com/cockroachdb/cockroach/pull/103323)