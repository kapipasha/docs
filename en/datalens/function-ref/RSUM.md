---
editable: false
---

# RSUM

_Window functions_

#### Syntax {#syntax}


```
RSUM( value [ , direction ] [ TOTAL | WITHIN [ dim1, ... ] | AMONG [ dim1, ... ] ] [ ORDER BY ... ] )
```

#### Description {#description}
Returns the sum of all values in a growing (or shrinking) window defined by the sort order and the value of `direction`:

| `direction`   | Window                                                 |
|:--------------|:-------------------------------------------------------|
| `"asc"`       | Starts from the first row and ends at the current row. |
| `"desc"`      | Starts from the current row and ends at the last row.  |

By default `"asc"` is used.


Window functions with a similar behavior: [RCOUNT](RCOUNT.md), [RMIN](RMIN.md), [RMAX](RMAX.md), [RAVG](RAVG.md).

See also [SUM](SUM.md), [MSUM](MSUM.md).

**Argument types:**
- `value` — `Number`
- `direction` — `String`


**Return type**: Same type as (`value`)

{% note info %}

Only constant values are accepted for arguments (`direction`).

{% endnote %}

{% note warning %}

The sorting order is based on the fields listed in the chart's sorting section and in the function's `ORDER BY` clause. First, `ORDER BY` fields are used, and then they are complemented by the fields from the chart.


{% endnote %}


#### Examples {#examples}

```
RSUM([Profit])
```

```
RSUM([Profit], "asc")
```

```
RSUM([Profit] TOTAL)
```

```
RSUM([Profit], "desc" WITHIN [Date])
```

```
RSUM([Profit] AMONG [Date])
```


#### Data source support {#data-source-support}

`Materialized Dataset`, `ClickHouse 1.1`, `Microsoft SQL Server 2017 (14.0)`, `MySQL 5.6`, `PostgreSQL 9.3`.
