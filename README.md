wp-cli/role-command
===================

Manage user roles and capabilities.

[![Build Status](https://travis-ci.org/wp-cli/role-command.svg?branch=master)](https://travis-ci.org/wp-cli/role-command)

Quick links: [Using](#using) | [Installing](#installing) | [Contributing](#contributing)

## Using

This package implements the following commands:

### wp role create

Create a new role.

~~~
wp role create <role-key> <role-name> [--clone=<role>]
~~~

**OPTIONS**

	<role-key>
		The internal name of the role.

	<role-name>
		The publicly visible name of the role.

	[--clone=<role>]
		Clone capabilities from an existing role.

**EXAMPLES**

    # Create role for Approver.
    $ wp role create approver Approver
    Success: Role with key 'approver' created.

    # Create role for Product Administrator.
    $ wp role create productadmin "Product Administrator"
    Success: Role with key 'productadmin' created.



### wp role delete

Delete an existing role.

~~~
wp role delete <role-key>
~~~

**OPTIONS**

	<role-key>
		The internal name of the role.

**EXAMPLES**

    # Delete approver role.
    $ wp role delete approver
    Success: Role with key 'approver' deleted.

    # Delete productadmin role.
    wp role delete productadmin
    Success: Role with key 'productadmin' deleted.



### wp role exists

Check if a role exists.

~~~
wp role exists <role-key>
~~~

Exits with return code 0 if the role exists, 1 if it does not.

**OPTIONS**

	<role-key>
		The internal name of the role.

**EXAMPLES**

    # Check if a role exists.
    $ wp role exists editor
    Success: Role with ID 'editor' exists.



### wp role list

List all roles.

~~~
wp role list [--fields=<fields>] [--format=<format>]
~~~

**OPTIONS**

	[--fields=<fields>]
		Limit the output to specific object fields.

	[--format=<format>]
		Render output in a particular format.
		---
		default: table
		options:
		  - table
		  - csv
		  - json
		  - count
		  - yaml
		---

**AVAILABLE FIELDS**

These fields will be displayed by default for each role:

* name
* role

There are no optional fields.

**EXAMPLES**

    # List roles.
    $ wp role list --fields=role --format=csv
    role
    administrator
    editor
    author
    contributor
    subscriber



### wp role reset

Reset any default role to default capabilities.

~~~
wp role reset [<role-key>...] [--all]
~~~

**OPTIONS**

	[<role-key>...]
		The internal name of one or more roles to reset.

	[--all]
		If set, all default roles will be reset.

**EXAMPLES**

    # Reset role.
    $ wp role reset administrator author contributor
    Success: Reset 1/3 roles.

    # Reset all default roles.
    $ wp role reset --all
    Success: All default roles reset.



### wp cap add

Add capabilities to a given role.

~~~
wp cap add <role> <cap>...
~~~

**OPTIONS**

	<role>
		Key for the role.

	<cap>...
		One or more capabilities to add.

**EXAMPLES**

    # Add 'spectate' capability to 'author' role.
    $ wp cap add author spectate
    Success: Added 1 capability to 'author' role.



### wp cap list

List capabilities for a given role.

~~~
wp cap list <role> [--format=<format>]
~~~

**OPTIONS**

	<role>
		Key for the role.

	[--format=<format>]
		Render output in a particular format.
		---
		default: list
		options:
		  - list
		  - table
		  - csv
		  - json
		  - count
		  - yaml
		---

**EXAMPLES**

    # Display alphabetical list of Contributor capabilities.
    $ wp cap list 'contributor' | sort
    delete_posts
    edit_posts
    level_0
    level_1
    read



### wp cap remove

Remove capabilities from a given role.

~~~
wp cap remove <role> <cap>...
~~~

**OPTIONS**

	<role>
		Key for the role.

	<cap>...
		One or more capabilities to remove.

**EXAMPLES**

    # Remove 'spectate' capability from 'author' role.
    $ wp cap remove author spectate
    Success: Removed 1 capability from 'author' role.

## Installing

Installing this package requires WP-CLI v0.23.0 or greater. Update to the latest stable release with `wp cli update`.

Once you've done so, you can install this package with `wp package install wp-cli/role-command`.

## Contributing

We appreciate you taking the initiative to contribute to this project.

Contributing isn’t limited to just code. We encourage you to contribute in the way that best fits your abilities, by writing tutorials, giving a demo at your local meetup, helping other users with their support questions, or revising our documentation.

### Reporting a bug

Think you’ve found a bug? We’d love for you to help us get it fixed.

Before you create a new issue, you should [search existing issues](https://github.com/wp-cli/role-command/issues?q=label%3Abug%20) to see if there’s an existing resolution to it, or if it’s already been fixed in a newer version.

Once you’ve done a bit of searching and discovered there isn’t an open or fixed issue for your bug, please [create a new issue](https://github.com/wp-cli/role-command/issues/new) with the following:

1. What you were doing (e.g. "When I run `wp post list`").
2. What you saw (e.g. "I see a fatal about a class being undefined.").
3. What you expected to see (e.g. "I expected to see the list of posts.")

Include as much detail as you can, and clear steps to reproduce if possible.

### Creating a pull request

Want to contribute a new feature? Please first [open a new issue](https://github.com/wp-cli/role-command/issues/new) to discuss whether the feature is a good fit for the project.

Once you've decided to commit the time to seeing your pull request through, please follow our guidelines for creating a pull request to make sure it's a pleasant experience:

1. Create a feature branch for each contribution.
2. Submit your pull request early for feedback.
3. Include functional tests with your changes. [Read the WP-CLI documentation](https://wp-cli.org/docs/pull-requests/#functional-tests) for an introduction.
4. Follow the [WordPress Coding Standards](http://make.wordpress.org/core/handbook/coding-standards/).


*This README.md is generated dynamically from the project's codebase using `wp scaffold package-readme` ([doc](https://github.com/wp-cli/scaffold-package-command#wp-scaffold-package-readme)). To suggest changes, please submit a pull request against the corresponding part of the codebase.*
