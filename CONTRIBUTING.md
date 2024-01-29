# CONTRIBUTING.md

1. We use the [fork and pull](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests#fork--pull) model to manage changes. More information about [forking a repository](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo) and [making a Pull Request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).
2. Create a new branch from and submit pull requests against the main branch.
   When editing, you need only commit changes to the Markdown source files.
3. If you're looking for things to work on, please see the [list of issues](https://github.com/crosschain-alliance/documentation/issues) for this repository. Comments on issues and reviews of pull requests are equally welcome.

## Build

To build the lessons locally, install the following:
[Gitbook](https://github.com/GitbookIO/gitbook/blob/master/docs/setup.md)
Install the Gitbook plugins:

```
$ gitbook install
```

Then build the pages and start a web server to host them:

```
$ gitbook serve
```

You can see your local version by using a web-browser to navigate to http://localhost:4000 or wherever it says it's serving the book.
