# Github Actions

## What is github actions ?

- Platform to automate developer workflows
  `CICD Tool` --> One of the many workflows

  ### What are the workflows ?

  - The organizational tasks have a lot of `organizational tasks` to manage.

    - Suppose you created a library in JAVA and some `contributors` and some `users` of the library and when `user` sees the new release of library has a `bug` they can create an `issue` that something is not working.  
      Check whether :  
      a) Is it minor/major ?  
      b) Is it reproducible ?  
      c) Assign to a contributor

    - The contributor fixes the issue and creates a `pull request` so that you can merge it in the next release of the library. Then

    1. Review the pull request
    2. Is the bug fixed ?
    3. Merge it to the master branch

    - After the pull request is merged in the master branch, you want to build a pipeline that will merge your code, build your artifact and so on.

    1. Prepare some release notes to indicate what got edited in the new version
    2. Update the version

    The below figure depicts these are the workflow examples of what one has to do as the maintainer of such repositories
    ![Screenshot 2024-05-08 131255](https://github.com/kaustubhchile/git_practice_test/assets/72078555/7b234cd9-dd91-49d0-93e3-efe173b50df3)

    Bigger the project gets and the more contributors you get and more the features and issues they fix and the pull request they create and more the people use your porject, the more organizational effort it would be.

    As a developer you wont want to do this tedious organizational stuff.So one would want to automate as much as possible of the management tasks so that you can also focus on programming and developing new features and functionalities in the project.

    For this purpose github actions were created

  ## How github actions automate these workflows ?

  - Every time something happens in your repository or to your repository, one can configure automatic actions to get executed in response.
  - These things that are happening in your repository or to your repository are called `Github Events`
  - Someone creating a pull request or an issue or someone joining as a contributor or merging pull request in the master branch is an event.

  So when you automate these flows :

  1. One listens to any such events and depending on what event happens, you want a certain workflow to execute automatically. So everytime someone creates an issue that is an event, maybe one wants to automatically sort the issue,
     label it or assign it to the contributor or write a script or test that will automatically try to reproduce the issue.
  2. So all these things can be automated with actions. So each small task that you automatically trigger on an event will be considered as a separate action.
  3. These combination of actions make up a workflow.
     ![Screenshot 2024-05-08 165304](https://github.com/kaustubhchile/git_practice_test/assets/72078555/ea004a10-ef3a-4a8c-8f13-30a6fba2b38e)

  ## CI/CD with Github Actions

  Most common workflow that one can think for their repository would be a CI/CD pipeline  
  For example:

  ```
  Step 1: Commit your code
  Step 2: Tests your code
  Step 3: Build starts. It tests your code and builds it into an artifact.
  Step 4: Pushes the artifact in some storage.
  Step 5: Deploys applicatiion on a deployment server
  ```

  ![Screenshot 2024-05-08 171331](https://github.com/kaustubhchile/git_practice_test/assets/72078555/8bfe7a71-6394-461f-afcb-3e369eae2f63)

  ### Advantage of Github Actions

  1.  If code already hosted on github, one can use the same tool for CI/CD pipeline as well as now no need to set up a third party tool and manage it separately as it is integrated in your code repository.
  2.  Set up process of CI/CD pipeline is very easy
  3.  Tool for developers so no need of an extra person who is dedicated for setting up and maintaining that CI/CD pipeline.

  ### Why is setup easy ?

  When you think about CI/CD pipeline, one of the most important thing is its integration with other technologies. Eg:-

  ![Screenshot 2024-05-08 172841](https://github.com/kaustubhchile/git_practice_test/assets/72078555/0e4c0abd-9c14-4e13-99c8-1f159d2f0992)

  So one shouldn't be involved in trying to configure out your CI/CD pipeline with tools such as installing JAVA, Maven ,Docker and configuring integrations and plugins.  
  Instead you directly want an environment with Node and Docker both available without the user installing any of it with a specific version and doint the deployment part by simply connecting to target and deploying the application there.

  ![Screenshot 2024-05-08 172841](https://github.com/kaustubhchile/git_practice_test/assets/72078555/63497329-488c-47d3-ad0b-a22dd9c63d9d)

  ## CI/CD Demo

  Java Gradle project build into a docker image and pushed to our private docker repository.

  ![Screenshot 2024-05-08 173822](https://github.com/kaustubhchile/git_practice_test/assets/72078555/e641d042-4412-424d-bbf5-ca69aa5a7894)

  First get the java application using gradle project(Here basically forked the project and removed the .github/workflows folder)

  ![Screenshot 2024-05-08 175806](https://github.com/kaustubhchile/git_practice_test/assets/72078555/7588b21b-51e7-4b11-b33a-fb3ee40dd2e6)

  Then go to Actions

  ![Screenshot 2024-05-08 180055](https://github.com/kaustubhchile/git_practice_test/assets/72078555/4418494a-4b08-4c28-b880-8a52ca418aea)

  Here you will find the list of `workflow templates` so one doesnt need to write a workflow file from scratch. Use the template corresponding to the technology your project uses

  ![Screenshot 2024-05-08 180310](https://github.com/kaustubhchile/git_practice_test/assets/72078555/d37f9d81-0595-427b-af43-b073f75d1bae)

  Then choose JAVA with Gradle workflow template

  ![Screenshot 2024-05-08 181059](https://github.com/kaustubhchile/git_practice_test/assets/72078555/5114fa4c-c959-4a92-9951-08fa16301a4c)

  In github workflows whenever refering to `actions`, we use the attribute `uses` and whenever running a `linux command` we use the attribute `run`.

  ![Screenshot 2024-05-09 195102](https://github.com/kaustubhchile/Music-app-player/assets/72078555/bf01268e-5a49-42fa-aa74-b653a26d376b)

  After creating the workflow file, click on `commit changes` and then select `create a new branch` and then click on `Propose Changes` and then create a `Create pull request` that will be merged with the master branch.

  ![Screenshot 2024-05-09 195900](https://github.com/kaustubhchile/Music-app-player/assets/72078555/f4c8aaa0-a6c4-416a-b584-1a03cbbafbe1)

  ![Screenshot 2024-05-09 200255](https://github.com/kaustubhchile/Music-app-player/assets/72078555/c58e1902-b38a-43ad-b9b9-23dea657dcdf)

## Github Actions

- Its a built in `CI/CD` Tool for Github. CI/CD basically allows us to automate the testing of our code to make sure it meets certain criteria. After all the tests are passed one can enable actions to automate the delivery of the code. This can significantly reduce the time it takes for you to deliver updates to your applications which allows developers to focus more of their time on the code itself.

  ![Screenshot 2024-06-23 151944](https://github.com/kaustubhchile/Music-app-player/assets/72078555/cbabb6b1-a518-4580-a411-5085d66dfe15)

- We have a workflow YAML File which specifies the following:

  - Events:

    - It is a trigger for a workflow. A common event that occurs in a repository is when someone pushes new code. One can see that in this configuration file we specify the `on:push` in workflow to trigger when someone pushes new code.

  ![Screenshot 2024-06-23 201339](https://github.com/kaustubhchile/Music-app-player/assets/72078555/cd61ca96-5684-44e6-9328-9bc938c90ff4)

  ```
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

    - In the `runs-on` parameter we specify the runner. It is basically a container environment that will run the code. By default github runs the container for you but one can host their own runner. The default containers to choose from are ubuntu linux, microsoft windows and mac-os.

  - Steps:

    - Underneath the steps there are 2 actions that are being run.

  - Actions:
    - First it will do `Checkout Code` job and then it is going to run the`Run Super-Linter` job against it.

  So to put it all together on the event that someone pushes new code, its going to run the job `super-lint`. That job will run on a ubuntu container hosted on github.com and then it will go through 2 steps. The first step is to check out the code and the next step is to run the linter.

  ```
    Linter is something that one uses to make sure that the code is conforming to certain standards.
    Super-Linter is made up of multiple linters
  ```

  ### To create a workflow

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
