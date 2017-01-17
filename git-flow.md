<!---
    // TODO: cheatsheet

    http://danielkummer.github.io/git-flow-cheatsheet/
-->

## Git Flow

Git-flow are a set of git extensions to provide high-level repository operations for Vincent Driessen's branching model.

### Init

Start using git-flow by initializing it inside an existing git repository

```
git flow init
```

### Feature

```
git flow feature start new-branch-name
```

This action creates a new feature branch based on 'develop' and switches to it.


```
git flow feature finish existing-branch-name
```

Finish the development of a feature. This action performs the following:

- merges MYFEATURE into `develop`
- removes the feature `branch`
- switches back to `develop branch`


```
git flow feature publish existing-branch-name
```

Are you developing a feature in collaboration? Publish a feature to the remote server so it can be used by other users.