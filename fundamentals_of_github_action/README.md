## Fundamental Building Block for GitHub Action

- There are `3 main building blocks for GitHub Action`:
  
  - `Workflow` :- 
    - `defined on the repo level` , when we want to `create the workflow` then `we need to define that under a repo`
    - we can define which trigger actually start the workflow, for example, `on push` or `on pull request` or `on schedule` etc.
    - `workflow` is a collection of `one or more jobs`
  
  - `Job` :- 
    - `defined on the workflow level` , when we want to `create the job` then `we need to define that under a workflow` , we `can't create job without defining the workflow`
    - `we can define which runner actually run the job`, for example, `ubuntu-latest` or `windows-latest` or `macos-latest` etc. we will learn about the `options` and `possibility` that can define different environment
    - by default , `job` run in `parallel` but we can define the `dependency` between the jobs and make them run in `sequential` order
    - `job` is a collection of `one or more steps`
  
  - `Steps` :- 

    - `defined on the job level` , when we want to `create the step` then `we need to define that under a job` , we `can't create step without defining the job`
    - the `steps` define the actual script or command or github Action that we want to run in the job, for example, `run npm install` or `run npm test` etc. 
    - `step` is a collection of `one or more actions`
    
    - By default, `steps` run in `sequential` order `but we can define the` `condition` `for each step and make them run in` `parallel` `or` `conditionally` `based on the requirement`.

    - if we want to `run the steps in parallel` then we can define them under different jobs and make those jobs run in parallel, for example, if we want to `run the test cases in parallel` then we can define different jobs for different test cases and make those jobs run in parallel.

### Difference Between `Github Actions` , `workflows` and `Github Action`

- GitHub Actions :- `GitHub Actions` is a `CI/CD` platform i.e `feature provided by GitHub(workflows , custom actions and many other feature provided by GitHub)` , that allows you to `automate your software development workflows` directly in your GitHub repository. It provides a way to `build, test, and deploy your code` based on various events and triggers.

- Workflow :- `Workflow` is a `defined process` that consists of `one or more jobs` and is `triggered by specific events`. It is defined in a YAML file within the `.github/workflows` directory of your repository. A workflow can be triggered by events such as `push`, `pull request`, `schedule`, etc., and it defines the sequence of jobs and steps to be executed.

- GitHub Action :- `GitHub Action` is a `reusable unit of code` that can be used in a `workflow to perform a specific task`. It can be a `predefined action provided by GitHub Marketplace` or a `custom action created by the user` or `action defined in a separate repository` . `rather than define the shell command on the steps of a Workflow job we can use actions` as well. Actions can be used to perform various tasks such as `checking out code`, `setting up the environment`, `running tests`, etc. Actions can be defined in a separate repository and can be shared and reused across different workflows and repositories.


```yaml

.github/workflows/my-workflow.yaml
==================================

name: My Workflow
on: push

# here even though we have defined 2 jobs but they will run in parallel because we haven't defined any dependency between them

# the job will run in different runner of same type(ubuntu-latest) and they will run in parallel by default but we can define the dependency between the jobs and make them run in sequential order

jobs:

  my-first-job:
    runs-on: ubuntu-latest
    steps:
      - run : echo "Hello World"
  
  my-second-job:
    runs-on: ubuntu-latest
    steps:
      - run : echo "Bye World"

```