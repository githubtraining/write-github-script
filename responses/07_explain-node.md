# Improving the issue comment

💡Did you know that GitHub Script also grants you access to a full Node.js environment?

Although we wouldn't recommend using GitHub Script to write the logic for complex actions, there are use cases where you may want to leverage using a little more than just the octokit/rest.js API.

One such use case is our issue comment. Right now it is pretty hard coded the way it is making it less than ideal. What if we wanted to display our contribution guide every time an issue was opened?

Instead of writing the guide directly into our workflow, we can use the Node.js File System module to read a file and use it as the body of our issue comment.

If we want access to the files within our repository, we need to make sure we include the `actions/checkout` action in our workflow as the first step.
