# vergilii
Your guide through the complexities of software projects. A curated playbook of principles, checklists, and strategies for senior engineers and tech leads.

## Project Kick-off

### Project Kick-off: Core Questions

* [ ] **Cloud & Account:** Which provider (AWS, GCP, Azure)? Existing client account or new?
* [ ] **Authentication & Authorization:** What is the primary auth model for cloud services? (e.g., IAM Roles, Service Accounts).

## Good coding practices

* Instantly update the changelog with new information.
* Use [C4 model](https://c4model.com/) to model an architecture. You can draw blueprints in [structurizr](https://structurizr.com/).
* [YAGNI](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it)
  * Write extensible code, but only add the functionalities needed now.
* If your changes are not ready to be submitted at the end of your work day, make a dirty branch, commit all of your changes to it (typically git commit -am'WIP') and push it to a remote.
* TDD works only when you fully understand the problem and interface. Building a thing is a good way to explore.
* You should set up a clear naming convention at the beginning of your project and stick to it. 
