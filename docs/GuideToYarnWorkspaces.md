# Guide to Yarn (2.0+) Workspaces

[Official documentation](https://yarnpkg.com/features/workspaces)

## Overview of Yarn workspaces

Yarn workspaces are a way to have multiple projects within the same monorepo.
Workspaces are organized into worktrees where each workspace is a node in the
worktree. For this purpose, the root of a monorepo is a workspace itself and
can be referred as the **project-level** workspace.

### Workspace benefits

Workspaces have a few primary benefits over separating packages into separate
repos:

1. Modification to the codebase of one workspace will be reflected to all other
   workspaces in the worktree.
2. Workspace dependencies are local to that workspace but may be deduped from
   the package manager. Developers can also focus only on a specific workspace
   and use those dependencies only.
3. Will prefer local workspace packages over remote packages (will not be used
   for our case since we are not publishing these packages).

## How to use Yarn workspaces

### Declaring workspaces

1. Create a workspace directory.
2. Add some matching pattern for the workspace directory into the `workspaces`
   array to the `package.json` of the nearest ancestor.
3. Setup the workspace directory.
   1. If you are using a create-app initializer, direct the initializer to set
      up the project in the workspace directory.
   2. If you are setting up the workspace from scratch, add a `package.json` to
      the workspace directory and add a key-value pair for the `name` property.
      The value will be the workspace name.
4. **(Optional)** Initialize the workspace by editing `package.json` or running
   `yarn workspace [workspace name] init` and other variations to edit the
   manifest.

### Using workspaces

You can run any yarn command in a given workspace as

```
yarn workspace [workspace name] init
```

For example, to add the `test` package to a workspace named `test123`, you can
run the following command:

```
yarn workspace test123 add test
```

These commands can be run anywhere in the project as long as the workspace can
be found in the worktree.

You can also run a script specified elsewhere such if it has a prefixed with a
specific name and a colon (eg. `test:test123`). However, it will run in the
CWD instead of the workspace that the yarn script originates from.

## References.

1. [Yarn official docs on workspaces](https://yarnpkg.com/features/workspaces)
2. [Yarn official docs on the cli](https://yarnpkg.com/cli/run#details)