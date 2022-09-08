# Mergify Usage

## What is Mergify

Mergify is a bot used to automatically handle the status pull requests and
perform fast-forward merges (something GitHub does not support). This maintains
a linear commit history so we can more easily identify the history of the
development by removing merge commits.

## How to use Mergify

At this point in time, there are three requirements at which point the Mergify
bot will automatically fast-forward merge the branch to main.
* It has been approved by one person with write, maintain, or admin permissions
* The feature branch has a linear commit history
* There are no conflicts with the main branch

Once Mergify merges the branch into main, the pull request should be closed
and merged. This is a new tool and the documentation did not specify how it
gets closed.

If edits to the behavior of the Mergify bot need to be made, the configuration
file for Mergify is in `.github/mergify.yml` with the
[official docs on the Mergify website](https://docs.mergify.com/configuration/).