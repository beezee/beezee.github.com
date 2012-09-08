---
layout: post
title: "Pre Commit Hook Wishlist: What my future code review process will look like"
category: Development
tags: ['source-control', 'best-practices', 'code-review']
---
{% include JB/setup %}

Inspired by [this handy gist](https://gist.github.com/3623562) I'm going to take a moment and get my thoughts on paper about
what my pre-commit hook of tomorrow will look like, because we keep adding developers and I don't get any more excited about
reading diffs.

*   Get a list of all changed files
*   Enforce presence of standard test suite in directory of each changed file
*   Ensure all tests pass
*   Get a test coverage listing into the diff

In a perfect world, I will only have to check that a) modified code has test coverage, and b) test coverage for modified code
properly exercises the code that was modified. I'll already know the tests pass by virtue of the fact the commit was accepted.

Going on my todo list right now...