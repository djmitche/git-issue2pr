git-issue2pr
============

A command-line tool to convert GitHub issues into pull requests by supplying code for them.
This is based on http://issue2pr.herokuapp.com/, but without the need for pointing and clicking.

Usage
-----

First, create a personal-access token (GitHub -> Settings -> Applications)

    git config issue2pr.token [your token here]

Hack away in a topic branch named after the issue, e.g., `issue123` for #123.
When your work is complete, push to your repo on github, then

    git issue2pr

That's it!

### Repositories

The tool assumes that your repository is at a remote named `origin`, and that the issue is in a repository pointed to by the `upstream` remote.
If either is not the case, simply set `issue2pr.origin` or `issue2pr.upstream`, respectively, to point to the appropriate remote or URL.
For example:

    git config issue2pr.upstream https://github.com/djmitche/git-issue2pr.git

or (if the `my-repo` remote points to your GitHub repository)

    git config issue2pr.origin my-repo

### Issue Number

If you don't name your topic branches after the corresponding issue, you can give `issue2pr` an explicit issue number to convert:

    git issue2pr --issue 345

### Base Branch

By default, the tool assumes that the pull request should be made against the upstream `master` branch.
If this isn't the case, use the `--branch` argument:

    git issue2pr --base development
