# Require a repository to be 30 days old before it can be added

Schema: `tinychange`, from https://github.com/speclib/openspec-tinychange-schema
(install it with the guide in that repo's AGENT_INSTALL.md).

Bean: awesome-openspec-0u7g (01 List curation and growth).

A repository that is a few days old cannot be judged: there is no way to tell a
tool that will be maintained from a weekend experiment. Thirty days is the same
threshold the awesome manifesto sets for a list before it may be submitted, so
it is a number that can be pointed at in a review.

The rule is a submission gate, not a pruning rule. It decides what enters the
list, and says nothing about entries that are already in it. Enforcement is by
review: `lint.yml` runs remark over `README.md` with no network access, so it
cannot read a repository's creation date.

A pull request below the threshold is closed rather than parked. The project has
no triage queue in use, and closing with the eligible date puts the waiting on
the contributor instead of on the maintainer.

## 1. Implementation

- [x] 1.1 In `CONTRIBUTING.md`, add a guideline directly after "Make sure the resource is related to OpenSpec or Spec-Driven Development" stating that a GitHub repository must have existed for at least 30 days, that a pull request adding a younger repository is closed with the date on which it becomes eligible and can be reopened on or after that date, and that articles, videos and other published resources count from their publication date instead.
- [x] 1.2 Create `.github/PULL_REQUEST_TEMPLATE.md` with a checklist covering the 30 day repository age (with a "not applicable" option for entries that are not repositories), the 150 character line limit, alphabetical placement within the section or subsection, and a working link.

## 2. Verification

- [x] 2.1 Capture the `npm run lint` baseline first, then run it again after the edit and confirm no NEW warnings. Remark exits 0 on warnings, so read the output rather than trusting the exit code. `README.md` is untouched by this change, so the two runs should be identical.
- [x] 2.2 Confirm the template sits at exactly `.github/PULL_REQUEST_TEMPLATE.md`, which is the path GitHub reads, and that it renders as four separate checkboxes rather than one paragraph.
- [x] 2.3 Read the new `CONTRIBUTING.md` guideline back and confirm it names the three parts of the rule: the 30 day threshold, what happens to a younger pull request, and the exemption for resources that are not repositories.
- [x] 2.4 Run `nix flake check`.
