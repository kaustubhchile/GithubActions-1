# Github Actions

- Its a built-in `CI/CD` Tool for GitHub. CI/CD basically allows us to automate the testing of our code to make sure it meets certain criteria. After all the tests are passed one can enable actions to automate the delivery of the code. This can significantly reduce the time it takes for you to deliver updates to your applications which allows developers to focus more of their time on the code itself.

  ![Screenshot 2024-06-23 151944](https://github.com/kaustubhchile/Music-app-player/assets/72078555/cbabb6b1-a518-4580-a411-5085d66dfe15)

- We have a workflow YAML File which specifies the following:

  - Events:

    - It is a trigger for a workflow. A common event that occurs in a repository is when someone pushes new code. One can see that in this configuration file we specify the `on:push` in workflow to trigger when someone pushes new code.

  ![Screenshot 2024-06-23 201339](https://github.com/kaustubhchile/Music-app-player/assets/72078555/cd61ca96-5684-44e6-9328-9bc938c90ff4)

  ```yml
  name: Super-Linter

  on: push

  jobs:
    super-lint:
      name: Lint code base
      runs-on: ubuntu-latest
      steps:
        - name: Checkout code
          uses: actions/checkout@v2

        - name: Run Super-Linter
          uses: github/super-linter@v4
          env:
            DEFAULT_BRANCH: main
            GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
  ```

  - Jobs:

    - When the event occurs, it is going to run all the jobs within the workflow. In the below workflow we have a single job named `super-lint` that specifies multiple steps and actions.

  - Runners:

    - In the `runs-on` parameter we specify the runner. It is basically a container environment that will run the code. By default GitHub runs the container for you but one can host their own runner. The default containers to choose from are ubuntu linux, microsoft windows and mac-os.

  - Steps:

    - Underneath the steps there are 2 actions that are being run.

  - Actions:
    - First it will do `Checkout Code` job and then it is going to run the`Run Super-Linter` job against it.

  So to put it all together on the event that someone pushes new code, its going to run the job `super-lint`. That job will run on a ubuntu container hosted on GitHub.com and then it will go through 2 steps. The first step is to check out the code and the next step is to run the linter.

  ```bash
    Linter is something that one uses to make sure that the code is conforming to certain standards.
    Super-Linter is made up of multiple linters
  ```

## To create a workflow

First go to the repository then click on `Add File`-->`Create New File`

![Screenshot 2024-06-23 234703](https://github.com/kaustubhchile/Music-app-player/assets/72078555/c3be0e76-b2e5-43c6-9bb6-93fc62ca5c8e)

Then we have to be very specific with the naming here. The proper directory structure for your workflow file is
`.github/workflows` and then name the file whatever you want.

![Screenshot 2024-06-24 015937](https://github.com/kaustubhchile/Music-app-player/assets/72078555/bfe7fb47-fc3c-4c58-b2ca-8209a0dedac5)

And then we can copy and paste the above code here(for yaml file)

![Screenshot 2024-06-24 020240](https://github.com/kaustubhchile/Music-app-player/assets/72078555/39708234-1af2-4235-b0f2-2da1708d855e)

and then commit your changes.

In the below figure, the yellow dot indicates that the workflow is currently running and checking the code.

![Screenshot 2024-06-24 104022](https://github.com/kaustubhchile/git_practice_test/assets/72078555/7e000943-fe86-4b22-b567-4f08f029b2fd)

If all the checks pass then it will turn to green and if the checks fail then it will turn red.

Then click on the `actions`(or click on the `yellow dot`)

![Screenshot 2024-06-24 104336](https://github.com/kaustubhchile/git_practice_test/assets/72078555/ca927275-34be-497d-859e-5c9667bee118)

In the `actions` tab, you can see the `super-linter` workflow is running

![Screenshot 2024-06-24 105033](https://github.com/kaustubhchile/Cloud-storage-application/assets/72078555/c2d521d9-cac5-4400-abf5-76278321e15d)

If all the workflow checks have passed, we get a green check mark like this:

![Screenshot 2024-06-24 112455](https://github.com/kaustubhchile/GithubActions-1/assets/72078555/9216a99c-7406-425c-a117-c7d6ce1ce5a3)

![Screenshot 2024-06-24 112808](https://github.com/kaustubhchile/GithubActions-1/assets/72078555/0fdd5982-6eb6-459a-8471-b3a4ac018ef9)

Now we will generate some code that will generate some linting error.

So we create a new file(like we created workflow file) and paste the following code:

```python
define hello():
  print("hello")

define bye():
    print("bye")

print(hello())
```

The below code is wrong as it has some wrong indentation. So the `linter` workflow will fail it.

![Screenshot 2024-06-24 115805](https://github.com/kaustubhchile/GithubActions-1/assets/72078555/5befd775-b6e8-4df5-8f3f-d0de68b5dadb)

The yellow dot indicates that the workflow is triggered again.

![Screenshot 2024-06-24 120311](https://github.com/kaustubhchile/GithubActions-1/assets/72078555/9f397a61-adb1-4f16-9f52-b53a360efca2)

![Screenshot 2024-06-24 120607](https://github.com/kaustubhchile/GithubActions-1/assets/72078555/dc41c417-e301-4cde-bcc7-e83ba6cb2885)

As expected there is an error in the workflow.

We can also see errors that occured in the workflow during its execution and how to fix those errors:

![Screenshot 2024-06-24 133754](https://github.com/devopsjourney1/mygitactions/assets/72078555/1210c07f-02ce-4060-a24e-82d65f825e33)

![Screenshot 2024-06-24 134035](https://github.com/devopsjourney1/mygitactions/assets/72078555/2898a750-f55f-4a77-afe5-7e73c5914b03)

So now we fix the errors and see the result:

Now we update the changes:

![Screenshot 2024-06-24 134251](https://github.com/devopsjourney1/mygitactions/assets/72078555/ee46888e-1c71-447a-91ce-8eca0c7354b7)

Now the workflow is triggered again:

![Screenshot 2024-06-24 134348](https://github.com/devopsjourney1/mygitactions/assets/72078555/37417e99-7b8f-402f-a2a4-5066d1ee1d59)

And now there are no errors.

![Screenshot 2024-06-24 134512](https://github.com/devopsjourney1/mygitactions/assets/72078555/7c5959b0-fe67-4734-9611-cac85380224e)

Here we have the history of all our workflow jobs.

![Screenshot 2024-06-24 134743](https://github.com/devopsjourney1/mygitactions/assets/72078555/8a98a62e-9069-4d72-a903-b03d9da5a2f0)

One can have multiple workflows in a single GitHub repository.

If one wants to go through a guided setup instead of writing file from scratch, we can go to `New Workflow` right here

![Screenshot 2024-06-24 135330](https://github.com/devopsjourney1/mygitactions/assets/72078555/65e23153-7b8e-4510-8831-45f45a94f296)

and then one will find a lot of templated options.

![Screenshot 2024-06-24 135539](https://github.com/devopsjourney1/mygitactions/assets/72078555/010207e5-e499-4e4b-8d00-66fed908caa2)
