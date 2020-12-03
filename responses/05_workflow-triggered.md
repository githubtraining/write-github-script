## Great job @{{user.login}}

Now that your updates have been merged and we've triggered the workflow we should see our workflow begin helping us automate the triage of new issues.

<details>
  <summary>Workflow not running? Click here for some troubleshooting.</summary>

Try the following troubleshooting steps:
1. Click on the [Actions tab]({{ store.actionsUrl }}) to see the status of your workflow run. See [Managing a workflow run](https://help.github.com/en/actions/configuring-and-managing-workflows/managing-a-workflow-run) on GitHub Help for more information.
1. Edit your [workflow file]( {{ store.workflowEditUrl }}) and look for errors in the linter built into the browser.
1. Look for the [workflow trigger](https://help.github.com/en/actions/reference/events-that-trigger-workflows) and ensure you are performing an action that triggers that workflow.

If you need to make changes to your code, remove the [main branch protection]({{ store.branchSettingsUrl }}) and merge your changes into the `main` branch.
</details>

---

I'll respond once your workflow has completed!
