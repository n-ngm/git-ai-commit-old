# ai-commit-message
This script generates git commit message from staged diff using GhatGPT.

## Installation

### Homebrew
```bash
$ brew untap n-ngm/tap
$ brew tap n-ngm/tap
$ brew install n-ngm/tap/git-ai-commit
```

## Options

| Option | Description |
| --- | --- |
| --api-key         | OpenAI API key (default: $OPENAI_API_KEY environmental variable). |
| --model           | OpenAI model (default: gpt-4o-mini). |
| --temperature     | OpenAI Temperature for sampling (default: 0.7). |
| --lang            | Language for output (default: \$LANG environmental variable else en-US). |
| --body-lines      | Number of lines for body (default: 0 = none). |
| --non-interactive | Do not prompt for confirmation (default: no). |
| --help            | Show this help message. |

## Example:

Basic usage:
```
$ git add .

$ git ai-commit
refactor: improve code structure for better readability
OK ? [y/n/q]: n

feat: enhance code organization for improved clarity
OK ? [y/n/q]: y

[write_readme 59ea82a] feat: enhance code organization for improved clarity
 1 file changed, 36 insertions(+)

```

Other options:
```
$ git ai-commit --lang jp --body-lines 2 --model gpt-3.5-turbo --temperature 0.3
feat: より良い可読性のためのコード構造の改善

- この変更は、コードの構造を改善し、可読性を向上させるためのものです。
- また環境変数の変更を行いました。
OK ? [y/n/q]:
````

## Set Git alias (recommended)

Add the following to your `.gitconfig` file:
```
[alias]
    ac = ai-commit
    ace = ai-commit -e
```
