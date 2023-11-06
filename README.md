# gh-approve-prs

This is an extension for [GitHub CLI](https://cli.github.com/) that approves and merges multiple PRs.
It is useful in repositories that use a GitHub merge queue.

The tool will attempt to approve and then merge each PR that:

* match a provided query - e.g. `--query "author:app/dependabot"` so that only Dependabot PRs are processed
* and have checks passing

## Installation

Prerequisites:
* [GitHub CLI](https://cli.github.com/) is already installed and authenticated
* [`jq`](https://stedolan.github.io/jq/) is installed

To install this extension:

```
gh extension install mbiggs-gresham/gh-approve-prs
```

## Usage

```
cd $DIRECTORY_OF_YOUR_REPO

gh approve-prs --query "QUERY"
```

### Required arguments
    --query "QUERY"
            sets the query used to find combinable PRs.
            e.g. --query "author:app/dependabot"
            to combine Dependabot PRs

### Optional arguments
    --selected-pr-numbers COMMA,SEPARATED,LIST
            if set, will only work on PRs with the selected numbers.
            e.g. --selected-pr-numbers 42,13,78
            Defaults to selecting every PR matching the QUERY
    --limit LIMIT
            sets the maximum number of PRs that will be approved.
            Defaults to 50
    --skip-pr-check
            if set, will approve matching PRs even if they are not passing checks.
            Defaults to false when not specified
    --skip-approve
            if set, will not approve the PR. (Useful for merging only)
            Defaults to false when not specified
    --skip-merge
            if set, will not merge the PR. (Useful for approving only)
            Defaults to false when not specified

## License

See [LICENSE](./LICENSE)
