# ai-commit-message
This script generates git commit message from staged diff using GhatGPT.

## Installation

### Homebrew
```bash
$ brew untap n-ngm/tap
$ brew tap n-ngm/tap
$ brew install n-ngm/tap/ai-commit-message
```

## Options

| Option | Description |
| --- | --- |
| -k, --api-key | OpenAI API key (default: $OPENAI_API_KEY environment variable). |
| -l, --lang | Language for output (default: $LANG environment variable else en-us). |
| -b, --body-lines | Add number of bullet points for body (default: 0). |
| -n, --non-interactive | Do not prompt for confirmation (default: no). |
| -h, --help | Show this help message. |

## Set Git alias (recommended)

Add the following to your `.gitconfig` file:
```
[alias]
    ai-commit = ! git commit -m \"$(ai-commit-message -l en)\"
    ai-commit-edit = ! git commit -e -m \"$(ai-commit-message -l en)\"
```

example:
```
$ git add README.md
$ git ai-commit
feat: Add ai-commit-message tool for generating git commit messages from staged diff.
OK ? [y/n/q]: n
feat: Add README.md with installation instructions and options for generating git commit messages.
OK ? [y/n/q]: y
[write_readme 59ea82a] feat: Add README.md with installation instructions and options for generating git commit messages.
 1 file changed, 36 insertions(+)
 create mode 100644 ai-commit-message/README.md
```
