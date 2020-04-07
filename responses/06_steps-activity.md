# Add steps for each action

We will make the following changes to the current workflow file:

- Name each step so we can easily keep track of it in the [actions tab]({{store.actionsUrl}})
- Use expressions to determine `if` a step should execute

### :keyboard: Activity: Add newly opened issue to project board

1. [Edit]({{quicklink}}) the current workflow `.github/workflows/my-workflow.yml` to have the following contents:

   ```yaml
   name: Learning GitHub Script

   on:
     issues:
       types: [opened]

   jobs:
     comment:
       runs-on: ubuntu-latest
       steps:
       - name: Comment on new issue
         uses: actions/github-script@0.8.0
         with:
           github-token: {% raw %}${{secrets.GITHUB_TOKEN}}{% endraw %}
           script: |
               github.issues.createComment({
               issue_number: context.issue.number,
               owner: context.repo.owner,
               repo: context.repo.repo,
               body: "🎉 You've created this issue comment using GitHub Script!!!"
               })

       - name: Add issue to project board
         if: contains(github.event.issue.labels.*.name, 'bug')
         uses: actions/github-script@0.8.0
         with:
           github-token: {% raw %}${{secrets.GITHUB_TOKEN}}{% endraw %}
           script: |
               github.projects.createCard({
               column_id: {{columnID}},
               content_id: context.payload.issue.id,
               content_type: "Issue"
               });

   ```

2. Commit the workflow to a new branch.
3. Create a pull request, I suggest the title **Create better comments**.
4. Supply the pull request body content and click **Create pull request**.

---

I am waiting for you to create a new pull request before moving on.

I'll respond in the pull request you create
