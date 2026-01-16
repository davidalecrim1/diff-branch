# Diff Branch - Claude Code Commands

A collection of git diff commands for Claude Code that help you understand branch changes quickly. Similar to Cursor IDE's branch comparison feature.

## Overview

These commands allow Claude to gather context by comparing your current branch with other branches using git diff. Perfect for code reviews, understanding what changed, or getting Claude up to speed on your work.

## Available Commands

### `/diff-master`

Compare your current branch with the master branch.

```
/diff-master
```

This command will:
- Show all changes from where your branch diverged from master
- Provide a summary of modified files
- Highlight key changes and patterns
- Give you context about what's different

### `/diff-branch`

Compare your current branch with any other branch.

```
/diff-branch <branch-name>
```

**Examples:**
```
/diff-branch develop
/diff-branch feature/login
/diff-branch main
```

This command will:
- Show all changes compared to the specified branch
- Analyze the differences and provide insights
- Help you understand what's unique in your current branch

## Installation

Install this plugin in Claude Code by running:

```
/plugin marketplace add https://github.com/davidalecrim1/diff-branch
```

## Why Use These Commands?

- **Code Reviews**: Quickly understand what changed in a branch
- **Context Building**: Get Claude up to speed on your changes before asking questions
- **Branch Comparison**: See differences between any two branches
- **Workflow Enhancement**: Similar to Cursor IDE's branch comparison, now in Claude Code

## Technical Details

Both commands use `git diff <branch>...HEAD` (three-dot syntax) to properly compare from the merge-base point where branches diverged, giving you accurate and meaningful diffs.

## License

MIT

## Author

David Alecrim (david.socer@hotmail.com)

## Contributing

Feel free to open issues or submit pull requests to improve these commands!
