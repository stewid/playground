# playground
Experimental repository

## Test to clone and push with `git2r`

### clone

```
library('git2r')
repo <- clone("git@github.com:stewid/playground.git", "./playground")
```

Make changes...

```
add(repo, "README.md")
commit(repo, "Commit with git2r")
push(repo)
```
