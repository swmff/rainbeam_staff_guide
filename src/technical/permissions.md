# Permissions

Rainbeam expresses permissions using bitflags which join together into a single, serializable integer.

You can view the names of every permission [here](https://swmff.github.io/rainbeam/authbeam/permissions/struct.FinePermission.html), with their values visible in the source [here](https://github.com/swmff/rainbeam/blob/6d4f98e5ea360757b4cbe9424293b89bc1732408/crates/authbeam/src/permissions.rs#L7-L43).

These permissions are demoed in the [`moderation.sql`](https://github.com/swmff/rainbeam/blob/6d4f98e5ea360757b4cbe9424293b89bc1732408/sql/moderation.sql) example. In this example, we create a default "helpers" group:

```sql
INSERT INTO
    "xgroups"
VALUES
    ('Helpers', '1', 33603612);
```

This group is given a permission integer of `33603612`, which is built using something similar to the following:

```js
(1 << 2) | (1 << 3) | (1 << 4) | (1 << 14) | (1 << 15) | (1 << 25)
```

That represents the following permissions:

- `MANAGE_RESPONSES`
- `MANAGE_COMMENTS`
- `MANAGE_QUESTIONS`
- `VIEW_AUDIT_LOG`
- `VIEW_REPORTS`
- `MANAGE_WARNINGS`

This also matches the [minimum permissions to be marked as a "helper"](https://github.com/swmff/rainbeam/blob/6d4f98e5ea360757b4cbe9424293b89bc1732408/crates/authbeam/src/permissions.rs#L121-L128).
