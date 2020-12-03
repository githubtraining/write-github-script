## That's not much different, so why might I want to use GitHub Script?

With GitHub Script you don't have to worry about

- Building a custom action to create this issue comment.
- No Octokit dependencies to worry about.
- No additional packages to manage.
- No need to write action metadata.
- No need to write source code to handle this Octokit method.

Using GitHub Script instead of writing custom actions for repository related tasks can prove to be a much more light-weight solution in most cases.

Anything you can do with Octokit can be accomplished with GitHub Script 🎉!

---

_You may have noticed that when using GitHub Script the method call starts with `github` and not `octokit`. This is because GitHub Script provides you with a pre-authenticated octokit/rest.js client stored in a variable named `github`._

_`context` is a reference to an object containing the [context of the current workflow run](https://github.com/actions/toolkit/blob/main/packages/github/src/context.ts)_
