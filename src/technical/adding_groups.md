# Adding user groups

In Rainbeam, each `Profile` contains a `group` field which determines the group that they are part of. Groups point to a row in the `xgroups` table.

As a starting point, we provide the [`moderation.sql`](https://github.com/swmff/rainbeam/blob/master/sql/moderation.sql) file to give you a simple setup.

This chapter will walk through what each line of that file does, and how you can customize it to create your own groups.

---

In the start of the file, we create three groups:

```sql
-- the minimum value for helpers is:
-- (1 << 2) | (1 << 3) | (1 << 4) | (1 << 14) | (1 << 15) | (1 << 25)
INSERT INTO
    "xgroups"
VALUES
    ('Helpers', '1', 33603612);

-- the minimum value for managers is:
-- (1 << 2) | (1 << 3) | (1 << 4) | (1 << 10) | (1 << 11) | (1 << 13) | (1 << 14) | (1 << 15) | (1 << 23) | (1 << 25)
INSERT INTO
    "xgroups"
VALUES
    ('Managers', '2', 42003484);

-- admins are granted administrator permissions:
-- (1 << 0) | (1 << 1)
INSERT INTO
    "xgroups"
VALUES
    ('Admins', '3', 3);
```

These groups are created using [bitflag permissions](./permissions.md).

The name and ID of a group **must** be unique to the group, but the roles can be shared with any group.

Finally, we add a user to the group:

```sql
UPDATE "xprofiles" SET "group" = '1' WHERE "username" = 'USERNAME_HERE';
```

Adding a user to a group can _also_ be done through the moderator UI, but it has to be done through plain SQL to set up your first administrator user.

The number that we change `group` to **must** correspond with a group from the `xgroups` table.
