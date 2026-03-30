# Introduction

## Purpose

The purpose of this site is to act as a "community guide", consisting of
how-tos and FAQs for things relating to THORChain.  This includes instructions
for how to achieve tasks on front-ends (such as THORSwap).

This site originally started as a GitHub Gist written exclusively by one
person.  Over time, more and more people began contributing information and
reviewing procedures.  At times, even official front-ends refer users to some
of the procedures here!

We hope that you find the information here beneficial.

## Technical details

The site is written entirely in
[Markdown](https://rust-lang.github.io/mdBook/format/markdown.html), and
rendered into HTML/CSS using [mdBook](https://rust-lang.github.io/mdBook/).

[Cloudflare](https://www.cloudflare.com/) and
[Cloudflare Pages](https://developers.cloudflare.com/pages/) are used for
DNS, content serving, and caching for speed.

Every time there is a commit pushed to the `master` branch of the official
GitHub repository, the site is automatically built and updated.

Anyone who wishes to contribute is welcome to do so via GitHub pull requests.
Contributors with a strong dedication to the site can be added as official
collaborators on GitHub, thus allowing them to commit directly (i.e. no PRs).

- GitHub repository: <https://github.com/koitsu/tcecosystem-guide>
- Branch: `master`
