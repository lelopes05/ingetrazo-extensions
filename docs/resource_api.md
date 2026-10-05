# Extension resource/library API (experimental)

The IngeTrazo core remains domain-neutral: it does not need to know what a
wall, profile, material, family or preset means.

## This block adds

- lightweight resource metadata separated from heavy payloads;
- multiple library/source descriptions (personal, project, shared, remote);
- stable resource references with optional versions;
- dependency graphs across resource types;
- cycle and missing-dependency protection;
- lightweight search that never loads the full resource;
- optional import/export capabilities.

The provider still owns the actual storage and domain format.

## Required provider methods

```python
list_resources()
get_resource(resource_id)
```

## Optional provider methods

```python
list_libraries()
get_dependencies(resource_id)
export_resource(resource_id)
import_resource(payload)
```

A universal package file format is intentionally left for a later block.
That lets real providers reveal what a portable bundle actually needs before
the core freezes a format.


## Portable bundles

`core.resource_bundle` adds the experimental `.iglib` container for exporting
one resource with its dependencies and importing it elsewhere. See
`docs/resource_bundle.md`.
