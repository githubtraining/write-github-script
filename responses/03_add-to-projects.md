# let's add a card to a project board

<!-- ## Project board

{{listProj}}

## Column list

{{listCol}} -->

### :keyboard: Activity: Add newly opened issue to project board

You can use [this link]({{quicklink}}) to easily edit this file.

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
              column_id: {{columnID}}
              content_id: context.payload.issue.id
              content_type: "Issue"
            });
```
