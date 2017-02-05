# stargaze

```
stargaze - gaze at repos you've starred

usage:
  stargaze fetch <github-user>   fetch (or refetch) your starred repos
  stargaze random [<n>]          fetch <n> random starred repos [default: 1].
```

This is a simple command line script to fetch random repos that you've starred
on GitHub. It's useful as inspiration for finding hack ideas, passing the
time, and rediscovering nifty projects I'd been meaning to revisit.

## Example

```console
$ stargaze random
https://github.com/carols10cents/rustlings
Small exercises to get you used to reading and writing Rust code

$ stargaze random
https://github.com/sobolevn/git-secret
:busts_in_silhouette: A bash-tool to store your private data inside a git repository.
```

## Installation

It's just a simple bash script. Download `stargaze` and put it on your PATH.

Alternatively, there's a Homebrew formula if you're on macOS:

```
brew install jez/formulae/stargaze
```

If you want to take it up a notch, you can even add an alias like this in your
bashrc/zshrc:

```
alias bored='stargaze random'
```

## Dependencies

This script requires that `jq` and `shuf` or `gshuf` is on your PATH. If it's
not check the installation instructions for your system:

- <https://stedolan.github.io/jq/>
- `brew install coreutils` (to get `shuf` on OS X)

## Usage

We're using the GitHub API, which means you can run into rate limiting issues.
For this reason, requests to the GitHub API are cached, and only read from the
cache.

First: initialize the cache:

```
stargaze fetch GITHUB_USER
```

This dumps a file to `$XDG_CACHE_HOME/stargaze/starred-repos.json`.

Whenever you feel like updating the cache (i.e., you've starred a bunch of new
repos), just re-run `stargaze fetch GITHUB_USER`

Second: ask for a random repo:

```
stargaze random
```

Alternatively, you can ask for more than one at a time:

```
stargaze random 10
```


## LICENSE

[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](https://jez.io/MIT-LICENSE.txt)

