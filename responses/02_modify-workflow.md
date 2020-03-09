## Edit the current workflow

Currently `my-workflow.yml` is not set up correctly for our use-case. Before we make any changes now is a good time to answer **what is GitHub Script?**

**GitHub Script**

[GitHub Script](https://github.com/actions/github-script) is a really awesome action that allows you to quickly interact with the GitHub API directly in your workflow!

You can think of this as a way to run simple functions without the need to build a bulky custom action to do so.

📖 See [octokit/rest.js](https://octokit.github.io/rest.js/) for the API client
documentation.

### :keyboard: Activity: Use GitHub Script in a workflow to comment on an issue

1. [Edit]({{workflowFile}}) the `.github/workflows/my-workflow.yml` so that it has the contents below:

   ```yaml
   name: Learning GitHub Script

   on:
     issues:
       types: [opened]

   jobs:
     comment:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/github-script@0.8.0
           with:
             github-token: {% raw %}${{secrets.GITHUB_TOKEN}}{% endraw %}
             script: |
               github.issues.createComment({
                 issue_number: context.issue.number,
                 owner: context.repo.owner,
                 repo: context.repo.repo,
                 body: "🎉 You've created this issue comment using GitHub Script!!!"
               })
   ```

1. Commit these file changes to this branch

---

I'll respond in this pull request once you make these changes.
