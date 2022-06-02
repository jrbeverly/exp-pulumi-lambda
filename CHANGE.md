# Pulumi Changelog

Metadata on the environment properties (volatile status?):

```
exec.kind: cli
git.author: Jonathan Beverly
git.author.email: ...
git.committer: Jonathan Beverly
git.committer.email: ...
git.dirty: true
git.head: ec3d5a5a63251dd884634e25b1f98c9be6b4b912
git.headName: refs/heads/main
vcs.kind: github.com
vcs.owner: jrbeverly
vcs.repo: exp-pulumi-lambda
```

Which is a schema in JSON like so:

```json
{
    "exec": "cli",
    "git": {
        "author": "Jonathan Beverly",
        "author.email": "...",
        "committer": "Jonathan Beverly",
        "committer.email": "...",
        "dirty": true,
        "head": "ec3d5a5a63251dd884634e25b1f98c9be6b4b912",
        "headName": "refs/heads/main",
    },
    "vcs": {
        "kind": "github.com",
        "owner": "jrbeverly",
        "repo": "exp-pulumi-lambda"
    }
}
```