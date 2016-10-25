## Git

<!---
    // TODO: table of contents

    https://try.github.io/levels/1/challenges/10
-->

### Init

```
git init
```

Initializes a repository in an existing directory. This will create `.git` hidden folder, a location where Git operates.

### Status

```
git status
```

Shows the working tree status.

### Add

```
git add some-file.txt
```

This command updates the index using the current content found in the working tree, to prepare the content `staged` for the next commit.

Wildcards are supported, e.g. `git add '*.txt'` or you can add all files by `git add .`

### Commit

```
git commit -m 'Some message'
```

Records changes to the repository. By using `-m` flag, a custom message will be added with commit.

### Log

```
git log
```

Shows commit logs.

### Remote add

```
git remote add origin some-url
```

Manages set of tracked repositories.

### Push

```
git push -u origin master
```

Updates remote refs along with associated objects.

### Pull

```
git pull origin master
```

Fetchs from and integrate with another repository or a local branch.

### Reset

```
git reset --soft HEAD~1
```

Flag `soft` will move HEAD 1 commit back and put changes as they were not commited yet, so you can commit them again.

```
git reset --hard HEAD~1
```

Flag `hard` will move HEAD 1 commit back and delete changes.
