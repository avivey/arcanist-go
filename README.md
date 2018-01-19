# Maintainer needed

I no longer use Phabricator nor Arcanis and I have no time to maintain this repository. If you would like to take ownership, please let me know by [opening a new issue](https://github.com/kalbasit/arcanist-go/issues/new).

# Phabricator's Arcanist Golang support.

This library provide Go support for
[Arcanist](https://github.com/phacility/arcanist). Initially, these were
submitted as [D12120](https://secure.phabricator.com/D12120),
[D12620](https://secure.phabricator.com/D12620) and
[D12621](https://secure.phabricator.com/D12621). Releasing as a
repository until those revisions are reviewed.

# Usage

Clone this repository and add it to the `.arcconfig` file of your
project and configure the linters through `.arclint`.

Example:

```
$ cat .arcconfig
{
    "load": [
        "../../github.com/kalbasit/arcanist-go"
    ],
    "phabricator.uri": "http://phabricator.nasreddine.com/",
    "repository.callsign": "GOACD",
    "unit.engine": "GoTestEngine"
}


$ cat .arclint
{
    "exclude": [
        "(^Godeps/)",
        "(^\\.arc/__*)",
        "(^\\.arc/.*)",
        "(^\\.gitmodules$)"
    ],
    "linters": {
        "chmod": {
            "type": "chmod"
        },
        "filename": {
            "type": "filename"
        },
        "gofmt": {
            "include": [
                "(\\.go$)"
            ],
            "type": "gofmt"
        },
        "golint": {
            "include": [
                "(\\.go$)"
            ],
            "type": "golint"
        },
        "govet": {
            "include": [
                "(\\.go$)"
            ],
            "type": "govet"
        },
        "json": {
            "include": [
                "(^\\.arcconfig$)",
                "(^\\.arclint$)",
                "(\\.json$)"
            ],
            "type": "json"
        },
        "merge-conflict": {
            "type": "merge-conflict"
        },
        "spelling": {
            "type": "spelling"
        },
        "text": {
            "exclude": [
                "(\\.go$)",
                "(^Makefile$)",
                "(^.travis.yml$)"
            ],
            "type": "text"
        }
    }
}
```

# License

All source code is licensed under the [Apache 2.0 license](LICENSE), the
same license as for the
[Arcanist](https://github.com/phacility/arcanist) project.
