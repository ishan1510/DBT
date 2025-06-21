# dbt Model Configuration Cheat Sheet

In dbt, each model file can be configured using the `{{ config(...) }}` Jinja function at the top of the SQL file. This allows you to set materializations, partitions, clustering, tags, pre/post hooks, and more—on a per-model basis.

---

## ✅ Complete Example: dbt Model with Full Configuration

```sql
{{ config(
    materialized = 'incremental',
    unique_key = 'id',
    schema = 'analytics',
    alias = 'my_custom_model_name',
    database = 'analytics_db',
    tags = ['finance', 'monthly'],
    post_hook = [
        "insert into model_audit_log values ('model_name', current_timestamp)"
    ],
    pre_hook = [
        "delete from temp_table where 1=1"
    ],
    enabled = true,
    docs = {
        show = true
    },
    persist_docs = {
        relation = true,
        columns = true
    },
    full_refresh = false,
    partitions = {
        field = 'event_date',
        data_type = 'date',
        granularity = 'day'
    },
    cluster_by = ['country', 'event_type'],
    sort = ['event_date'],
    dist = 'event_type',
    bind = false,
    transient = true
) }}

with source_data as (
    select * from {{ ref('raw_events') }}
)

select
    id,
    event_date,
    event_type,
    country
from source_data
```

## 📌 Common `config()` Parameters by Use Case

| Purpose                | Parameters                                      |
|------------------------|-------------------------------------------------|
| Materialization        | `materialized`, `incremental_strategy`, `unique_key` |
| Deployment Control     | `enabled`, `full_refresh`                      |
| Data Warehouse Specific| `cluster_by`, `dist`, `sort`, `bind`, `transient` |
| Metadata/Docs          | `tags`, `docs`, `persist_docs`                |
| Hooks                  | `pre_hook`, `post_hook`                       |
| Naming Overrides       | `schema`, `alias`, `database`                 |
"""
