# roles/github

This role acts as an helper for other roles to retrieve code from a
GitHub project, either as a plain clone, or through a specific release
tarball.

As such, this role has no main, and include the role without
specifying a task file will fail.

## Configuration

The configuration differs according to the sub-role in use (tarball or
git). However, some variables are commons:

- `github_repository`: the name of the github repo to fetch code from.
- `github_release`:  of the version to fetch, either by checkout (could be a branch, a tag, a commit id) or by tarball (release tag).
- `github_path`: path to put the code on the host.

### Tarball specific configuration
