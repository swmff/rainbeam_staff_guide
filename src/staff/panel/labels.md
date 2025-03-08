# Labels tab

The labels tab has two parts:

- The "This user" section
- The global label manager section

In the first section, you're able to add user labels (by ID) to the user. You're also able to remove their labels and view information about the labels attached via the label's respective buttons.

In the second section, you're able to create and delete user labels globally. **Note that deleting a label does _not_ remove it from profiles**. That would be hard to implement.

## Reserved labels

The labels below are reserved and will be used for various purposes (even if they don't actually exist in the `xlabels` table).

- `-1`: quarantined user (effectively a shadow-ban, fully removed from timelines)
