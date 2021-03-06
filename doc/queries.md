# Searching bugs

You can search bugs using a micro query language for both filtering and sorting. A query could looks like this:

```
status:open sort:edit
```

A few tips:

- query are case insensitive.
- you can combine as much qualifier as you want.
- you can use quotation for multi-word search term. For example, use `author:"René Descartes"` to search with a complete name.


## Filtering

### Filtering by status

You can filter bugs based on their status.

| Qualifier       | Example                             |
| ---             | ---                                 |
| `status:open`   | `status:open` matches open bugs     |
| `status:closed` | `status:closed` matches closed bugs |

### Filtering by author

You can filter based on the person who opened the bug.

| Qualifier      | Example                                                                          |
| ---            | ---                                                                              |
| `author:QUERY` | `author:descartes` matches bugs opened by `René Descartes` or `Robert Descartes` |
|                | `author:"rené descartes"` matches bugs opened by `René Descartes`                |

### Filtering by label

You can filter based on bug's label.

| Qualifier     | Example                                                                   |
| ---           | ---                                                                       |
| `label:LABEL` | `label:prod` matches bugs with the label `prod`                           |
|               | `label:"Good first issue"` matches bugs with the label `Good first issue` |

### Filtering by missing feature

You can filter bugs based on the absence of something.


| Qualifier  | Example                                |
| ---        | ---                                    |
| `no:label` | `no:label` matches bugs with no labels |

## Sorting

You can sort result by adding a `sort:` qualifier to your query.

### Sort by Id 

| Qualifier                  | Example                                              |
| ---                        | ---                                                  |
| `sort:id-desc`             | `sor:id-desc` will sort bugs by their descending Ids |
| `sort:id` or `sort:id-asc` | `sor:id` will sort bugs by their ascending Ids       |

### Sort by Creation time

You can sort bugs by their creation time.

Note: to deal with badly set clocks in a distributed system, `git-bug` use a logical clock internally rather than timestamp to order bugs edition over time. That means that the timestamps recorded might not match the returned ordering. More on that in [the documentation](model.md#you-cant-rely-on-the-time-provided-by-other-people-their-clock-might-by-off-for-anything-other-than-just-display)

| Qualifier                               | Example                                                            |
| ---                                     | ---                                                                |
| `sort:creation` or `sort:creation-desc` | `sor:creation` will sort bugs by their descending creation time    |
| `sort:creation-asc`                     | `sor:creation-asc` will sort bugs by their ascending creation time |

### Sort by Edition time

You can sort bugs by their edition time.

Note: to deal with badly set clocks in a distributed system, `git-bug` use a logical clock internally rather than timestamp to order bugs edition over time. That means that the timestamps recorded might not match the returned ordering. More on that in [the documentation](model.md#you-cant-rely-on-the-time-provided-by-other-people-their-clock-might-by-off-for-anything-other-than-just-display)

| Qualifier                       | Example                                                            |
| ---                             | ---                                                                |
| `sort:edit` or `sort:edit-desc` | `sor:edit` will sort bugs by their descending last edition time    |
| `sort:edit-asc`                 | `sor:edit-asc` will sort bugs by their ascending last edition time |