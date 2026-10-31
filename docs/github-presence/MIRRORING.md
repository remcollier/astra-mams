# One-way GitLab → GitHub mirroring

Proposed setup, not executed. Use one mirror per repository.

## Workflow

Developers push and merge on GitLab. GitLab pushes commits to GitHub. Visitors browse or clone from GitHub and follow CONTRIBUTING to propose changes on GitLab. Never edit mirrored files directly on GitHub, including README changes.

GitHub organisation profile content is the exception: the separate `.github` repository is maintained there and is not a mirror.

## Setup after the GitHub repositories exist

1. Finish README and contribution-policy changes upstream first. Verify licences, branch scope, historical contents and external dependencies.
2. Create an empty GitHub repository for each source repository, without generating a README, licence or .gitignore. Keep it private during initial verification if public readiness is still being checked.
3. Create a fine-grained GitHub token restricted to those destination repositories with Contents read/write. Workflow write permission is also required if mirrored commits include `.github/workflows`. Store the credential only in GitLab's mirror settings, never in a tracked file or a clone URL committed to documentation.
4. In the GitLab project, open Settings → Repository → Mirroring repositories. Add the destination `https://github.com/ORGANISATION/REPOSITORY.git`, choose Push, and enter the token owner's username and token in the authentication fields.
5. Use the full reviewed public branch set initially. If selecting protected branches instead, first define which branches qualify and check resulting branch and tag coverage; protection status is not a substitute for a publication policy.
6. Select Keep divergent refs to make accidental GitHub edits produce a visible mirror failure rather than silently losing them. Resolve any divergence upstream and restore mirroring deliberately.
7. Trigger the first update. Compare branch and tag names and commit IDs across both hosts, inspect the rendered README, confirm the default branch, and clone anonymously once public. GitHub defaults and repository settings must be configured separately.
8. Disable GitHub Issues, Discussions and Wiki; set the website to the guide; add descriptions, topics and pins. Protect normal development from direct GitHub edits while ensuring the mirror credential can perform required updates. Test the actual rules before relying on them.
9. Push an ordinary documentation change upstream and confirm it reaches GitHub. Verify a tag on the next intended upstream release. Check source links and submodule/LFS availability where applicable.

GitLab documents push mirrors on its Free tier. Updates are asynchronous; do not promise an immediate copy. GitLab CI and package publishing remain unchanged.

## Operation and recovery

Check the mirror's last successful update and error status after initial setup, credential rotation and releases. A failed mirror must be fixed at the source or in its configuration; do not patch GitHub independently. A maintainer should own credential expiry and mirror failures. Automated alerts can follow once an owner and channel are agreed.

If an unexpected commit appears on GitHub, stop and inspect it. Preserve any useful work as a patch and apply it through GitLab before realigning the destination. Do not run blanket force pushes or `git push --mirror` against a repository containing independent work.

To stop mirroring, disable the GitLab push mirror and revoke its credential. The GitHub copy remains until separately removed. Public history cannot be made private retroactively for people who already cloned it.

## Separate future decisions

GitHub Releases, contribution intake on GitHub, GitHub Actions, package hosting and documentation hosting are separate from this mirror. Avoid adding them at launch. If GitHub later becomes the development home, plan a single cutover with issue/PR policy and redirects; avoid bidirectional mirroring.

Setup reference: [GitLab push mirroring documentation](https://docs.gitlab.com/user/project/repository/mirror/push/).
