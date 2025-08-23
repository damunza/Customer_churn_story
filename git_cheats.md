# Branch defaults

`master` is the name for the initial branch. 

This default branch name is subject to change. 

To configure the initial branch name call:

```bash
$ git config --global init.defaultBranch <name>
```
>  Names commonly chosen instead of `master` are `main`, `trunk` and `development`.
>

The just-created branch can be renamed via this command:

```bash
$ git branch -m <name>
```

To disable branch warning  messages use

```bash
 $ git config set advice.defaultBranchName false
```

