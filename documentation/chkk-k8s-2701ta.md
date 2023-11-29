---
title: CockroachDB crashes when executing query with AS OF SYSTEM TIME clause that uses an unspecified placeholder
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade CockroachDB to version `v20.2.2` or newer.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

This defect causes CockroachDB to crash and in turn can cause loss of service.

## Why does this exist? (Root Cause)

The crash happens when using an unspecified placeholder[1] value with `AS OF SYSTEM TIME` clause. The defect exists in the function `Type` that checks the placeholder type. If the placeholder is unspecified, the program panics with the message: “index out of bounds when accessing placeholder type”. For instance, executing a query such as 

```sql
select count(*) from t as of system time $1;
```

can crash CockroachDB as the placeholder `$1` is unspecified.

It has been fixed by checking if provided placeholder values is insufficient before accessing their type.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using CockroachDB versions `<= 20.2.1` contain this Latent Availability Risk.

## Additional Resources

For more information see:

- [Bug Fixes introduced in CockroachDB v20.2.2 release](https://www.cockroachlabs.com/docs/releases/v20.2#v20-2-2-bug-fixes)
- [The original GitHub issue](https://github.com/cockroachdb/cockroach/issues/56488)
- [The PR that fixed this issue](https://github.com/cockroachdb/cockroach/pull/56780)

[1] _A placeholder expression provides a location in a SQL statement for which a third-generation language bind variable will provide a value._