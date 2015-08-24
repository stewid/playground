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

## Another test with `git2r`

```r
library(git2r)
cred <- cred_ssh_key("~/.ssh/id_rsa.pub", "~/.ssh/id_rsa")
repo <- clone("git@github.com:stewid/playground.git", "playground", credentials = cred)
```

```r
#> cloning into 'playground'...
#> Receiving objects:   2% (1/48),    6 kb
#> Receiving objects:  12% (6/48),    6 kb
#> Receiving objects:  22% (11/48),    6 kb
#> Receiving objects:  31% (15/48),    6 kb
#> Receiving objects:  41% (20/48),    6 kb
#> Receiving objects:  52% (25/48),    6 kb
#> Receiving objects:  62% (30/48),    6 kb
#> Receiving objects:  72% (35/48),    6 kb
#> Receiving objects:  81% (39/48),    6 kb
#> Receiving objects:  91% (44/48),    6 kb
#> Receiving objects: 100% (48/48),    6 kb, done.
```

Make changes in README.md

```r
status(repo)
```

```r
#> Unstaged changes:
#>         Modified:   README.md
```

```r
add(repo, "README.md")
commit(repo, "Another test with git2r")
push(repo, credentials = cred)
```

## Test `cred_env` with `git2r`

Make changes in README.md

```r
add(repo, "README.md")
commit(repo, "Another test with git2r")
cred <- cred_env("GH_USER", "GH_PAT")
push(repo, credentials = cred)
```

## Test ssh with git2r on Windows

```r
library(git2r)
cred <- cred_ssh_key("~/.ssh/id_rsa.pub", "~/.ssh/id_rsa")
repo <- clone("git@github.com:stewid/playground.git", "playground", credentials = cred)
```

Make changes in README.md

```r
add(repo, "README.md")
commit(repo, "Test ssh with git2r on Windows")
push(repo, credentials = cred)
```

## Test ssh with git2r on OSX

Make changes in README.md

```r
> sessionInfo()
```

```r
#> R version 3.2.0 (2015-04-16)
#> Platform: x86_64-apple-darwin13.4.0 (64-bit)
#> Running under: OS X 10.10.1 (Yosemite)
#>
#> locale:
#> [1] C
#>
#> attached base packages:
#> [1] stats     graphics  grDevices utils     datasets  methods   base
#>
#> other attached packages:
#> [1] git2r_0.10.1.9000
#>
#> loaded via a namespace (and not attached):
#> [1] compiler_3.2.0 tools_3.2.0
```

## Test push with git2r

Make changes in README.md

```r
add(repo, "README.md")
commit(repo, "Test push with git2r", session = TRUE)
cred <- cred_env("GITHUB_USER", "GITHUB_TOKEN")
push(repo, credentials = cred)
```
