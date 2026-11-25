# GitHub Issues

Track issues and specs in `LucianoAMagalhaes/inventory-ledger-reconciliation`. Use the `gh` CLI from the repository root.

Before creating the first issue in a session, run `gh repo view --json nameWithOwner`. If it resolves to a different repository, confirm the target with the user.

## Ticket operations

- To publish a ticket or spec, run `gh issue create --title "<title>" --body-file <path>`.
- To fetch a ticket, run `gh issue view <number> --json number,title,body,labels,comments`.
- To list tickets, run `gh issue list --state open --json number,title,body,labels,comments`. Adjust `--state` and `--label` for the requested scope.
- To comment, run `gh issue comment <number> --body-file <path>`.
- To change labels, use `gh issue edit <number>` with `--add-label` or `--remove-label`.
- To close a ticket with an explanation, post the comment first, then run `gh issue close <number>`. Posting the comment separately also records the explanation on an already closed ticket.

## Parent issues and blockers

Use GitHub sub-issues to group tickets under a parent. Create a child with `gh issue create --parent <parent>` or link an existing child with `gh issue edit <parent> --add-sub-issue <child>`.

Use native issue dependencies to record blockers. Run `gh issue edit <child> --add-blocked-by <blocker>` for each dependency. A ticket is unblocked when every blocker is closed.

If the installed CLI lacks these flags, use the REST API. Obtain the child's or blocker's numeric database ID with `gh api 'repos/{owner}/{repo}/issues/<number>' --jq .id`.

- Link a child with `gh api --method POST 'repos/{owner}/{repo}/issues/<parent>/sub_issues' -F sub_issue_id=<child-db-id>`.
- Add a blocker with `gh api --method POST 'repos/{owner}/{repo}/issues/<child>/dependencies/blocked_by' -F issue_id=<blocker-db-id>`.
- Count open blockers with `gh api 'repos/{owner}/{repo}/issues/<child>' --jq .issue_dependencies_summary.blocked_by`.

If the tracker lacks sub-issues or dependencies, record the relevant relationship at the top of the child body using `Part of #<parent>` or `Blocked by: #<number>, #<number>`. Check each listed blocker's state before claiming the ticket.

## Pull requests as a triage surface

**PRs as a request surface: no.**

## Wayfinding

For `/wayfinder`, use one issue labeled `wayfinder:map`. Keep the map's notes, decisions so far, and open questions in its body.

- Link each ticket as a sub-issue and apply its type label (`wayfinder:research`, `wayfinder:prototype`, `wayfinder:grilling`, or `wayfinder:task`). If sub-issues are unavailable, use a task list in the map and a `Part of #<map>` line in the child.
- In map order, select the first open child with no assignee and no open blockers. Claim it with `gh issue edit <number> --add-assignee @me` as the session's first write.
- To resolve a ticket, comment with the answer, close the ticket, and add a summary and link to the map's decisions.
