# GITHUB-CI

Templates and examples for Github-CI

## Content

### Examples

* `examples/jenkins/.github/workflows/deploy-ENV.yaml`: Github Actions to build Jenkins jobs

---

### Using Github Actions to trigger the Jenkins jobs `deploy_devel` and `deploy_staging`
### Instructions

1. Copy and paste the `.github` folder inside `examples/jenkins` to your repository and create the `dev` and `production` branches if they do not exist.
2. In your github repo, access `Action secrets` (Secrets) in Settings, and create 3 new repository secrets: `JENKINS_USER`, `JENKINS_TOKEN` and `JENKINS_HOST`
  * To generate a `JENKINS_TOKEN` follow these instructions: https://www.jenkins.io/blog/2018/07/02/new-api-token-system/
  * The value of `JENKINS_USER` must be the same as the user who generated the `JENKINS_TOKEN`
  * `JENKINS_HOST` is the host of the Jenkins instance where the jobs will be built
3. Edit the `deploy-ENV.yaml` file inside the `.github` folder:

```yaml
jobs:
  launch_jenkins_deploy:
    name: Launch jenkins deploy-ENV job
    runs-on: ubuntu-latest
    env:
      GITHUB_REF: github.ref
      job_for_dev: ## Path inside Jenkins workspace to the deploy_devel job
      job_for_production: ## Path inside Jenkins workspace to the deploy_staging job
```
