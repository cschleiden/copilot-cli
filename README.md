# GitHub Copilot CLI Action

A composite GitHub Action that sets up Node.js, installs the GitHub Copilot CLI, and executes it with a provided prompt.

## Usage

```yaml
steps:
  - name: Execute Copilot CLI
    uses: cschleiden/copilot-cli@main
    with:
      prompt: "Write a function that calculates fibonacci numbers"
      PAT: ${{ secrets.GITHUB_TOKEN }}
    id: copilot
    
  - name: Display result
    run: echo "${{ steps.copilot.outputs.result }}"
```

## Inputs

| Input | Description | Required |
|-------|-------------|----------|
| `prompt` | The prompt to send to GitHub Copilot CLI | Yes |
| `PAT` | GitHub Personal Access Token for authentication | Yes |

## Outputs

| Output | Description |
|--------|-------------|
| `result` | The output from the GitHub Copilot CLI command |

## What it does

1. Sets up the latest version of Node.js
2. Globally installs the `@github/copilot` npm package
3. Executes `copilot -p <prompt>` with the provided GitHub token
4. Returns the command output as an action output

## Requirements

- The GitHub token must have appropriate permissions for Copilot access
- The repository/organization must have GitHub Copilot enabled
