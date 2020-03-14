## Use the FS module to use a templated comment

We will make the following changes to the current workflow file:

- Add the `actions/checkout` action so we can read the templated response file located at `.github/ISSUE_RESPONSES/comment.md`
- Add JavaScript to use the Node.js File System module to place the contents of our templated response as the body of the issue comment.

### :keyboard: Activity: Add newly opened issue to project board

1. [Edit]({{quicklink}}) the current workflow to have he following contents:

   ```yaml
   name: Learning GitHub Script

   on:
     issues:
       types: [opened]

   jobs:
     comment:
       runs-on: ubuntu-latest
       steps:
         - name: Checkout repo
           uses: actions/checkout@v2

         - name: Comment on new issue
           uses: actions/github-script@0.8.0
           with:
             github-token: {% raw %}${{secrets.GITHUB_TOKEN}}{% endraw %}
             script: |
                const fs = require('fs')
                const issueBody = fs.readFileSync(".github/ISSUE_RESPONSES/comment.md", "utf8")
                github.issues.createComment({
                issue_number: context.issue.number,
                owner: context.repo.owner,
                repo: context.repo.repo,
                body: issueBody
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

2. Commit the workflow changes to this branch.

---

I'll respond once you've committed the changes to this branch
