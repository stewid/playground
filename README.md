# playground
Experimental repository

## Test to clone and push with `git2r`

### clone

```r
library('git2r')
repo <- clone("git@github.com:stewid/playground.git", "./playground")
```

Make changes...

```r
add(repo, "README.md")
commit(repo, "Commit with git2r")
push(repo)
```

Show brief summary of commits

```r
invisible(lapply(commits(repo), show))
```

```r
#> [fb7b2b6] 2015-01-14: Commit with git2r
#> [46b881f] 2015-01-14: Initial commit
```
