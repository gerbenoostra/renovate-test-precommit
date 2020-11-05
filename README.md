# renovate-test-precommit
Repository to run renovate against

This repository holds a pre-commit config file with outdated versions. All of them should be detected by pre-commit.

Temporary workaround would be to configure renovate (`renovate.json`) using:

```json
{
  "regexManagers": [
    {
      "fileMatch": ["^.pre-commit-config.yaml$"],
      "matchStrings": [
        ".*repo: .*gitlab\\.com\\/(?<depName>\\S*)\\s*\\n\\s*rev: (?<currentValue>\\S*)"
      ],
      "versioningTemplate": "semver",
      "datasourceTemplate": "gitlab-tags"
    },
    {
      "fileMatch": ["^.pre-commit-config.yaml$"],
      "matchStrings": [
        ".*repo: .*github\\.com\\/(?<depName>\\S*)\\s*\\n\\s*rev: (?<currentValue>\\S*)"
      ],
      "versioningTemplate": "semver",
      "datasourceTemplate": "github-tags"
    }
  ],
}
```
