## Setting up your CI/CD infrastructure
### Configuring CI

Now that we have a file in our project, GitLab UI offers a "Set up CI" button:

![notice the "Set up CI" button](img/setup_ci.png)

---

## Setting up your CI/CD infrastructure
### Configuring CI

Select "Set up CI" to create the GitLab CI config file, `.gitlab-ci.yml` in the Web editor.

The GitLab CI configuration syntax is detailed
[here](https://docs.gitlab.com/ce/ci/yaml/README.html).

In addition to the Gitlab CI syntax, since the file is in YAML,
it has to follow the rules for [YAML](http://yaml.org).

There can be one `.gitlab-ci.yml` file per project and it lives at the top level.
---
## Setting up your CI/CD infrastructure
### Configuring CI

Edit your `.gitlab-ci.yml` (using the Web editor, next slide) to add a test job:


```console
test_it:
  script: /bin/echo I am a pretend test suite. I passed!
```
Reminder: If you're viewing this on gitpitch.com, "x" highlights the code block.


---
## Setting up your CI/CD infrastructure
### Configuring CI

Use the built-in Web editor:

![img](img/pretend_test_1.png)

Select "Commit changes" at the bottom, green.

---

## Setting up your CI/CD infrastructure
### Configuring CI

`script` lists the command the GitLab test runner will run to test your code.

Or, it could be a list of commands:

```console
my_CI_job:
  script:
  - make
  - make test
```


---


## Setting up your CI/CD infrastructure
### Configuring CI

Our first CI job, "test_it", will run on every commit 
to test the new revision. It will run the test command
we specified.

(It _is_ possible to run CI jobs on specific branches
only, e.g., only on merge requests into the "master" branch.
By default, GitLab runs CI on every commit,
to catch problems early.)

On the next slide, notice:
- that GitLab checked the syntax of the CI config file
- we haven't set up our Runner Server yet so there are no runners available to run the CI job, so we have an orange pause icon ("pending" indicator)

---?image=img/pending_pipeline.png

---
## Setting up your CI/CD infrastructure
### Configuring CI
Go to "CI/CD -> Pipelines" to see pipeline status:

![pipelines menu](img/pipelines_menu.png)

---
## Setting up your CI/CD infrastructure
### Configuring CI
You'll see the pipeline is "pending":

![stuck pipeline](img/stuck_pipeline.png)

Let's setup our CI/CD server yet.
