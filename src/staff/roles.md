# Group roles

Groups specify which _roles_ a user is given. Roles ([`authbeam::model::Permission`](https://swmff.github.io/rainbeam/authbeam/model/enum.Permission.html)) specify _what_ the user is actually allowed to do.

There are 3 roles available:

- [Admin](#admin)
- [Manager](#manager)
- [Helper](#helper)

## Admin

Admin users have the highest authority. They are able to manage the server and managers.

**Admins are able to promote other users to `Manager`**.

## Manager

Manager users have the second-highest authority. They are able to manage the server and helpers.

Managers are able to edit the sessions of regular users, as well as manage the settings that other users have set for their account.

**Managers are able to promote other users to `Helper`**.

## Helper

Helper users have the lowest authority (of the roles). They are able to manage assets and create user warnings.

An _asset_ is anything created on Rainbeam. This means that helpers can delete responses, comments, questions, chats, marketplace items, etc. Helpers can also view and manage reports and IP bans.

Despite all this power, helpers **cannot** view sensitive information about users, such as their session data. Helpers can also not manage the settings of users.
