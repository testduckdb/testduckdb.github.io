---
layout: docu
title: My Workload Is Slow
---

If you find that your workload in DuckDB is slow, we recommend performing the following checks. More detailed instructions are linked for each point.

1. Do you have enough memory? DuckDB works best if you have [5-10GB memory per CPU core](environment#cpu-and-memory).
1. Are you using a fast disk? Network-attached disks can cause the workload to slow down, especially for [larger than memory workloads](environment#disk).
1. Are you using indexes or constraints (primary key, unique, etc.)? If possible, try [disabling them](schema#indexing), which boosts load and update performance.
1. Are you using the correct types? For example, [use `TIMESTAMP` to encode datetime values](schema#types).
1. Are you reading from Parquet files? If so, do they have [row group sizes between 100k and 1M](file-formats#the-effect-of-row-group-sizes) and file sizes between 100MB to 10GB?
1. Does the query plan look right? Study it with [`EXPLAIN`](how-to-tune-workloads#profiling).
1. Is the workload running [in parallel](how-to-tune-workloads#paralellism)? Use `htop` or the operating system's task manager to observe this.
1. Is DuckDB using too many threads? Try [limiting the amount of threads](how-to-tune-workloads#parallelism-multi-core-processing).

Are you aware of other common issues? If so, please click the _Report Issue_ button above and describe them along with their workarounds.
