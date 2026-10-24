# ClockworkDigital's shared GitHub defaults

Future me: this repo gives ClockworkDigital repositories a shared set of issue forms, so we don't have to copy and maintain the same templates in every project.

The goal is simple: bug reports should explain how to reproduce the problem, and feature requests should explain the outcome someone wants.

## What's in here?

| File | What it asks for |
| --- | --- |
| [Bug report](.github/ISSUE_TEMPLATE/bug.yml) | Summary, steps to reproduce, expected result, actual result, and environment |
| [Feature request](.github/ISSUE_TEMPLATE/feature.yml) | Summary and desired outcome |

Every field in these forms is required when submitting through that form.

## How it works

GitHub treats a repository named `.github` as a place for account-wide defaults. When someone opens an issue in a ClockworkDigital repository that doesn't define its own issue templates or issue-template configuration, GitHub uses the forms here.

- The forms live on this repo's default branch, currently `main`.
- Changes here update the shared defaults; there's no copy or sync step.
- The inherited files don't appear in the receiving repo's file tree or clone.
- A repo with its own valid templates or configuration in `.github/ISSUE_TEMPLATE/` overrides the shared set entirely. GitHub doesn't merge its local forms with these.
- Required fields apply to these forms. This isn't a blanket validation rule for every issue created through other routes.

For ordinary GitHub organisations, this defaults repo must be **public**, even when the repositories using it are private. GitHub documents an internal-repo exception for organisations with managed users.

## Why the weird folder nesting?

The full path looks like this:

```text
ClockworkDigital/.github             ← the repository
└── .github/                         ← GitHub's configuration folder
    └── ISSUE_TEMPLATE/
        ├── bug.yml
        └── feature.yml
```

Yes, `.github` appears twice. The repository name and the folder inside it serve different purposes.

The form files also look like JSON despite having a `.yml` extension. That's intentional syntax-wise: JSON is valid YAML. They can be rewritten as ordinary YAML for readability.

## How to change things

1. Edit the relevant form in [`.github/ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE/).
2. Keep its name, description, field IDs, labels, and required-field settings valid for GitHub issue forms.
3. Commit the change to `main`, directly or through a pull request.
4. Open **Issues → New issue** in a repository that inherits these defaults and check that the forms appear and behave as expected. You don't need to submit an issue to preview the form.

For project-specific forms, create `.github/ISSUE_TEMPLATE/` in that project's repository and put its complete set of templates there. Remember that this replaces the inherited set for that repo.

If the shared forms aren't showing up, check that issues are enabled in the target repo, that it hasn't defined its own templates or configuration, and that this repo has the required visibility and the files are on its default branch.

## Reference

- [GitHub: default community health files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file)
- [GitHub: configuring issue templates](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository)

