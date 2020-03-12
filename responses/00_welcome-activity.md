## Configuring a workflow

Actions are enabled on your repository by default, but we still have to tell our repository to use them. We do this by creating a workflow file in our repository.

If you've been following the learning path for GitHub Actions then this task is quite familiar to you.

<details><summary>Brand new to GitHub Actions?  Click here to learn about workflows!</summary>

#### What is a workflow file?

A **workflow** file can be thought of as the recipe for automating a task. They house the start to finish instructions, in the form of `jobs` and `steps`, for what should happen based on specific triggers.

Your repository can contain multiple **workflow** files that carry out a wide variety of tasks. It is important to consider this when deciding on a name for your **workflow**. The name you choose should reflect the tasks being performed.

</details>

<br>

<!-- 💻 Actively learn about workflows by enrolling in [this Learning Lab course which has no name or content yet]() -->

📖 Read more about [workflows](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/configuring-a-workflow#choosing-the-type-of-actions-for-your-workflow)

### :keyboard: Activity: Respond to an issue when it get's opened

1. Create a new workflow file titled `.github/workflows/my-workflow.yml` with the following contents:
   You can use [this quicklink]({{quicklink}}) to easily create this file

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

1. Commit the workflow to a new branch.
1. Create a pull request titled **Create my-workflow.yml**.
1. Supply the pull request body content and click `Create pull request`.

_It is important to place meaningful content into the body of the pull requests you create throughout this course. This repository will stay with you long after you complete the course. It is advisable that you use the body of the pull requests you create as a way to take long lived notes about thing you want to remember._

<details><summary>Suggested body content</summary>

`Workflow files are the recipe for task automation. This is where actions are placed if I want to use them for a task.`

</details>

---

I'll respond in the new pull request when I detect it has been created.
