# git-ai-commit
This script is a git subcommand that generates a commit message using ChatGPT.

## Installation

### Install
Install using Homebrew (macOS and Linux).

```bash
$ brew untap n-ngm/tap
$ brew tap n-ngm/tap
$ brew install n-ngm/tap/git-ai-commit
```

Or, download the script, and put it into a directory in your PATH. (e.g. /usr/local/bin)
And make it executable.

```bash
$ curl -o /usr/local/bin/git-ai-commit https://raw.githubusercontent.com/n-ngm/tools/refs/heads/main/git-ai-commit/git-ai-commit
$ chmod +x /usr/local/bin/git-ai-commit
```

### OPENAI_API_KEY environment variable

Obtain an API key from OpenAI.  
https://platform.openai.com/api-keys

Set the obtained API key as an environment variable named OPENAI_API_KEY.  
It is recommended to add it to your shell profile.

```bash
export OPENAI_API_KEY="sk-....."
```

## Options

| Option | Description |
| --- | --- |
| `--api-key`         | OpenAI API key (default: $OPENAI_API_KEY environmental variable). |
| `--model`           | OpenAI model (default: gpt-4o-mini). |
| `--temperature`     | OpenAI Temperature for sampling (default: 0.7). |
| `--lang`            | Language for output (default: \$LANG environmental variable else en-US). |
| `--body-lines`      | Number of lines for body (default: 0 = none). |
| `--non-interactive` | Do not prompt for confirmation (default: no). |
| `--help`            | Show this help message. |

## Usage

### Basic usage

- You need to stage the changes with `git add`
- Generate a commit message with `git ai-commit`
- Review the generated message
  - Press `y` to commit with the generated message
  - Press `n` to regenerate the message
  - Press `q` to quit

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

### Customization

You can customize by using the options.

```
$ git ai-commit --lang jp --body-lines 2 --model gpt-3.5-turbo --temperature 0.3
feat: より良い可読性のためのコード構造の改善

- この変更は、コードの構造を改善し、可読性を向上させるためのものです。
- また環境変数の変更を行いました。
OK ? [y/n/q]:
```
