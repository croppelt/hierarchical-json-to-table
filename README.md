# hierarchical-json-to-table

Convert hierarchical, nested JSON to full table.

---

### Details

#### Task

Given a nested, hierarchical JSON (or Python `dict`), normalize it to a usable table representation such as a valid `pandas.DataFrame`.

#### Sample JSON

```python
po_dict = {'ABC': {"open": {},
                   "updated":
                       {"12": {"22334": 5, "22335": 5},
                        "01": {"22335": 1, "22336": 2, "22337": 2},
                        "02": {"22337": 8, "order": 2},
                        "03": {"order": 5}}},
            'DEF': {"open": {},
                    "updated":
                       {"12": {"22338": 5, "22339": 5},
                        "01": {"22339": 1, "22340": 2, "22341": 2},
                        "02": {"22341": 8, "order": 2},
                        "03": {"order": 5}}},
                    }

```

#### Expected result

```
material | state   | month | po_nb | po_value
---------------------------------------------
ABC      | open    |       |       |
ABC      | updated | 12    | 22334 | 5
ABC      | updated | 12    | 22335 | 5
ABC      | updated | 1     | 22335 | 1
ABC      | updated | 1     | 22336 | 2
ABC      | updated | 1     | 22337 | 2
ABC      | updated | 2     | 22337 | 8
ABC      | updated | 2     | order | 2
ABC      | updated | 3     | order | 5
DEF      | open    |       |       |
...
```
