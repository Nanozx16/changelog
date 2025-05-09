# changelog
Add way to verify each change has associated PRs (#222)
This commit adds a new option to the `validate` command, `--pr-links`,
which will cause an error to be thrown if:

- a changelog entry does not have one or more links to pull requests
after it
- a changelog entry does have PR links present, but they do not point to
the project's repo
- a changelog entry does have PR links present, but they are not
positioned at the very end of the line

The `ensureValidPrLinksPresent` option has also been added to
`validateChangelog`.

If this option is provided, then `parseChangelog` is instructed to look
for and extract pull request numbers from changelog entries. The list of
numbers will then be checked for in the validation step. It is also used
to reconstruct pull request links when the changelog is stringified.

Note that because this commit changes what `parseChangelog` returns,
this is a breaking change.
