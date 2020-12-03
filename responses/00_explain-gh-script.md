## Create an issue comment

If we take a look at the [Octokit documentation](https://octokit.github.io/rest.js/v17#issues-create-comment) on how to create issue comments we are greeted with the following method:

**someFile.js**

```javascript
octokit.issues.createComment({
  owner,
  repo,
  issue_number,
  body
});
```

Okay, that doesn't seem so hard. Now that we know how to do it with Octokit let's take a look at how to use GitHub Script to create an issue comment:

**my-workflow.yml**

```yaml
- uses: actions/github-script@0.8.0
  with:
    github-token: {% raw %}${{secrets.GITHUB_TOKEN}}{% endraw %}
    script: |
    github.issues.createComment({
        issue_number: context.issue.number,
        owner: context.repo.owner,
        repo: context.repo.repo,
        body: '👋 Thanks for reporting!'
    })
```

## Open a pull request

Now let's examine what it's like to open a pull request with octokit/rest.js:

**someFile.js**

```javascript
octokit.pulls.create({
  owner,
  repo,
  title,
  head,
  base
});
```

Again, that's not too hard at all. Now let's do the same thing, only using the GitHub Script action:

```yml
- uses: actions/github-script@0.8.0
  with:
    github-token: {% raw %}${{secrets.GITHUB_TOKEN}}{% endraw %}
    script: |
    github.pull.create({
        repo: github.context.repo.repo,
        owner: github.context.repo.owner,
        head: github.context.ref,
        base: "main",
        title: "from my action",
        body: "## I totally used GitHub Script to pull this off 🔥"
    })
```
