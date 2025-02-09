# Adding user groups

In Rainbeam, each `Profile` contains a `group` field which determines the group that they are part of. Groups point to a row in the `xgroups` table.

As a starting point, we provide the [`moderation.sql`](https://github.com/swmff/rainbeam/blob/master/sql/moderation.sql) file to give you a simple setup.

This chapter will walk through what each line of that file does, and how you can customize it to create your own groups.

---

In the start of the file, we create two groups:

```sql
INSERT INTO "xgroups" VALUES ('Moderators', '1', '["Helper"]');
INSERT INTO "xgroups" VALUES ('Admins', '2', '["Helper","Manager"]');
```

The first line creates a group named "Moderators" with an ID of `1` and _just_ the `Helper` [role](../staff/roles.md). You can change the ID of the group to anything, as long as it's a number.

The name and ID of a group **must** be unique to the group, but the roles can be shared with any group.

Finally, we add a user to the group:

```sql
UPDATE "xprofiles" SET "group" = '1' WHERE "username" = 'USERNAME_HERE';
```

Adding a user to a group can _also_ be done through the moderator UI, but it has to be done through plain SQL to set up your first administrator user.

The number that we change `group` to **must** correspond with a group from the `xgroups` table.
