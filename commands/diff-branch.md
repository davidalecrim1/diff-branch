---
description: Show all changes compared to any branch
argument-hint: <target-branch>
---

# Branch Context: Diff Against Any Branch

You are helping the user understand all changes in their current branch compared to a specified target branch. This is similar to Cursor IDE's @Branch feature and GitHub Copilot's "Branch (Diff with Main Branch)" context, but allows comparison with any branch.

## Getting the Target Branch

The target branch name will be provided as an argument after the command. If not provided, ask the user which branch to compare against.

## Your Task

Provide comprehensive context about the branch changes by running these commands in sequence:

### 1. Verify Target Branch and Get Current Branch
```bash
# Check if target branch exists
git rev-parse --verify <target-branch>

# Get current branch name
git branch --show-current

# Get current status
git status --short
```

If the target branch doesn't exist, inform the user and list available branches with `git branch -a`.

### 2. Get Branch Statistics
```bash
git diff --stat <target-branch>...HEAD
```

This shows files changed, insertions, and deletions.

### 3. Get Commit History
```bash
git log <target-branch>..HEAD --oneline --no-decorate
```

This shows all commits in the current branch that aren't in the target branch.

### 4. Get File Changes List
```bash
git diff --name-status <target-branch>...HEAD
```

This shows which files were modified (M), added (A), deleted (D), or renamed (R).

### 5. Get Full Diff
```bash
git diff <target-branch>...HEAD
```

This shows the complete code changes.

## How to Present the Information

Structure your response like this:

1. **Branch Overview**: Current branch name and comparison target
2. **Summary Statistics**: X files changed, Y insertions, Z deletions
3. **Commit History**: List of commits with messages
4. **Files Changed**: Organized list by change type (Added, Modified, Deleted)
5. **Key Changes**: Highlight the most significant modifications
6. **Patterns & Themes**: Identify what type of work was done (feature, bugfix, refactor, etc.)

## Important Notes

- Always use three-dot syntax `<target-branch>...HEAD` for proper merge-base comparison
- Verify the target branch exists before attempting diff
- If there are no changes, clearly state the branches are identical
- Focus on providing context that helps the AI understand the scope and nature of changes
- This context is meant to be consumed by AI to help with code reviews, documentation, or further development

## Usage Examples

- `/diff-branch develop` - Compare with develop branch
- `/diff-branch feature/login` - Compare with feature/login branch
- `/diff-branch main` - Compare with main branch
- `/diff-branch release/v2.0` - Compare with a release branch

## Example Output Structure

```
📍 Current Branch: feature/user-auth
📊 Comparing with: develop

Statistics:
- 5 files changed
- 156 insertions(+)
- 23 deletions(-)

Commits (2):
- abc123 Add JWT token validation
- def456 Update user schema

Files Changed:
Added:
- src/auth/validate.ts

Modified:
- src/types/user.ts
- src/api/auth.ts
- tests/auth.test.ts

Key Changes:
[Analysis of the most important changes]
```
