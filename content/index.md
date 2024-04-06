# Introduction

## Purpose

The purpose of this site is to act as a "community guide", consisting of
how-tos and FAQs for things relating to THORChain.  This includes instructions
for how to achieve tasks on front-ends (such as THORSwap).

While this site originally started as a GitHub Gist written exclusively by one
person, over time more and more people began contributing information and
reviewing procedures.  At times, even official front-ends refer users to some
of the procedures here!

We hope that you find the information here beneficial.

## Technical details

The site is written entirely in [Markdown], rendered using [mdBook], a
documentation-oriented static-site generator.

It is hosted using [GitHub Pages], with [Cloudflare] sitting in front of it for
added benefits of security and caching.

The site leverages [GitHub Actions]; every time there is a commit pushed to the
`master` branch of the official GitHub repository, the site auto-builds and
auto-updates.

Users who wish to make contributions are welcome to do so via pull requests.
Contributors with a strong dedication to the site can be added as official
collaborators on GitHub, thus allowing them to commit directly (i.e. no PRs).

- GitHub repository: <https://github.com/koitsu/tcecosystem-guide>
- Branch: `master`

[Cloudflare]: https://www.cloudflare.com/
[GitHub Actions]: https://docs.github.com/en/actions
[GitHub Pages]: https://pages.github.com/
[Markdown]: https://rust-lang.github.io/mdBook/format/markdown.html
[mdBook]: https://rust-lang.github.io/mdBook/
