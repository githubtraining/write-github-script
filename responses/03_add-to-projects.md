# let's add a card to a project board

We have added a project board to this repository for you. We will use this board, named **Learning Lab Project Board**, to add cards to when a new issue is created in your repository!

Like creating comments and opening pull requests, octokit/rest.js can be used for many more types of interactions. Managing GitHub Projects makes that list!

<details><summary>Things aren't always as they appear!</summary>
<br>
Although this is not a course on octokit/rest.js, it is important to tell you a little secret right here before we move on. For you to be able to use the `projects.createCard()` method there were some pieces of information we needed beforehand. Things like the `column_id` so we know which column to add the card to and even a `project_id` so we know which board that column belongs to.

We've gone ahead and done this on our end of things so that we could give you the final piece to the puzzle and demonstrate how to use GitHub Script. So if you try to recreate this on your own, without the help of Learning Lab you will need to get that information and parse it in a way that works well for your use case!

</details>

### :keyboard: Activity: Add newly opened issue to project board

1. [Edit]({{quicklink}}) the current workflow `.github/workflows/my-workflow.yml` to have he following contents:

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
               github.projects.createCard({
               column_id: {{columnID}},
               content_id: context.payload.issue.id,
               content_type: "Issue"
               });
   ```

2. Commit the workflow to a new branch.
3. Create a pull request titled **Update my-workflow.yml**.
4. Supply the pull request body content and click `Create pull request`.

---

I'll respond in the new pull request when I detect it has been created.
