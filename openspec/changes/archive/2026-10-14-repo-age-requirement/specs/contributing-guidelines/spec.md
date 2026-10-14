## ADDED Requirements

### Requirement: Contribution guidelines state a minimum repository age
CONTRIBUTING.md SHALL state that a GitHub repository must have existed for at
least 30 days before it can be added to the list. It SHALL state what happens
to a pull request that adds a younger repository: the pull request is closed
with the date on which the repository becomes eligible, and it can be reopened
on or after that date. It SHALL state that the age rule applies to
repositories only, and that articles, videos and other published resources
count from their publication date.

#### Scenario: Contributor reads the guidelines before submitting a repository
- **WHEN** a contributor reads CONTRIBUTING.md before opening a pull request that adds a GitHub repository
- **THEN** they SHALL find that the repository must have existed for at least 30 days

#### Scenario: Contributor submits a repository that is two weeks old
- **WHEN** a contributor reads CONTRIBUTING.md after their pull request was closed for being too new
- **THEN** they SHALL find that the pull request can be reopened once the repository reaches 30 days

#### Scenario: Contributor submits an article
- **WHEN** a contributor reads CONTRIBUTING.md before adding an article, video or other published resource
- **THEN** they SHALL find that the 30 day repository age rule does not apply to it

### Requirement: Pull requests open with a contribution checklist
The repository SHALL provide a pull request template at
`.github/PULL_REQUEST_TEMPLATE.md` holding a checklist of the contribution
requirements a reviewer checks: the minimum repository age with an opt out for
resources that are not repositories, the 150 character line limit, alphabetical
placement within the section or subsection, and a working link.

#### Scenario: Contributor opens a pull request
- **WHEN** a contributor opens a pull request against this repository on GitHub
- **THEN** the pull request body SHALL be prefilled with the contribution checklist

#### Scenario: Contributor adds a video
- **WHEN** a contributor works through the checklist for an entry that is not a GitHub repository
- **THEN** the age item SHALL offer a way to mark it as not applicable rather than forcing a false claim
