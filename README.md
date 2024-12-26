# Read Me

A test repo to mirror the way that Trac works using Labels in GitHub with GitHub Actions

## Issue Templates

There are 3 issue templates that are driven by the [base template](https://github.com/trac-dep-tests/label-based/blob/main/.github/ISSUE_TEMPLATE/base.yml). This allows a user to select the issue type when creating the issue AND it keeps the contents syncronized. If you need to make a change to an issue
template (for example to add a new version of Django) you would update the `base.yml` and a GHA will update the `bug.yml`, `cleanup.yml` and
`feature.yml` automatically

Labels will be added to the issue based on the data that is selected by the reporter, i.e. Easy Pickings, Has Patch,
etc.

The issue description will then be cleaned up to ONLY include what is entered into the Description field of the template

For example, if a user filled out this information:

![The original data entered by the user](/images/Original%20Data.png)

There is a clean up action that will remove everything other than the description to be this:

![The cleaned up data](/images/Cleaned%20Up%20Data.png)

## Assigning Issues

There are 2 assignment commands:

- `/take` - will make you the sole assignee of an issue
- `/assign` - will add you to the current list of assignees

The GHA that updates assignment cleans up after itself to keep the comment history clean

## Updating Labels

There are 3 label commands

- `/label` - adding a comment of `/label bug` will add the label of `bug`
- `/remove-label` - adding a comment of `/remove-label bug` will remove the
label of `bug`
- `/labels` 0 adding a comment of `/labels` will list all available labels

The GHA that updates labels cleans up after itself to keep the comment history clean

### Known Issues

1. Currently you can only add or remove one label at a time
2. You have to refresh the page to get the Labels to update. There is a bot message indicating the labels have been
updated though
