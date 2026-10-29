# Issue Tracker: GitHub

Issues and specs live in GitHub Issues for the working repository.
Use the `gh` CLI from this repository.

## Resolve the target repository

Use an explicitly requested repository when provided. Otherwise inspect
`git remote -v` and use the GitHub repository identified by `origin`.
In a fork, this normally means the fork's tracker. Treat an `upstream`
remote as a separate contribution target, not the default tracker.

Verify the resolved target with
`gh repo view <owner/repo> --json nameWithOwner,hasIssuesEnabled`.
If the intended target cannot be determined from the request and remotes,
ask which tracker to use. If Issues are disabled, report that limitation.

Pass the resolved `--repo <owner/repo>` explicitly to issue and label
commands. This avoids relying on GitHub CLI's locally configured default
repository. See the [CLI default-repository documentation](https://cli.github.com/manual/gh_repo_set-default).

## Conventions

- Create issues with
  `gh issue create --repo <owner/repo> --title "..." --body-file <path>`.
  Use a temporary file for multiline Markdown.
- Read issues with
  `gh issue view <number> --repo <owner/repo> --json number,title,body,labels,comments`.
- List issues with `gh issue list --repo <owner/repo> --state open`, filtering as needed.
- Apply or remove labels with `gh issue edit --repo <owner/repo>`.
- Add comments with `gh issue comment --repo <owner/repo> --body-file <path>`.
- Before closing an issue, post the resolution, then use `gh issue close --repo <owner/repo>`.
- Represent parent/child relationships and blockers with native GitHub
  sub-issues and dependencies. If unavailable, use `Part of #<number>`
  and `Blocked by: #<number>` in issue bodies.
- A ticket is ready only when all its blockers are closed.

When a skill says to publish to the issue tracker, create a GitHub issue.
When it says to fetch a ticket, read the corresponding GitHub issue.

## Pull Requests as a Triage Surface

PRs as a request surface: no.
