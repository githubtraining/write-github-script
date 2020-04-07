## Look 👀 at you!

Super awesome job so far!

Do you remember what our workflow trigger was?

```yaml
on:
  issues:
    types: [opened]
```

This means that every time an issue gets opened in this repository the GitHub Script you wrote will execute.

You should expect to see the result right here in this issue!

<details>
  <summary>Workflow not running? Click here for some troubleshooting.</summary>

Try the following troubleshooting steps:
1. Click on the [Actions tab]({{ store.actionsUrl }}) to see the status of your workflow run. See [Managing a workflow run](https://help.github.com/en/actions/configuring-and-managing-workflows/managing-a-workflow-run) on GitHub Help for more information.
1. Edit your [workflow file]( {{ store.workflowEditUrl }}) and look for errors in the linter built into the browser.
1. Look for the [workflow trigger](https://help.github.com/en/actions/reference/events-that-trigger-workflows) and ensure you are performing an action that triggers that workflow.

If you need to make changes to your code, remove the [master branch protection]({{ store.branchSettingsUrl }}) and merge your changes into the `master` branch.
</details>

---

I'll respond in this issue after your workflow runs!
