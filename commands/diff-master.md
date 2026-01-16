---
description: Show all changes in current branch compared to master
---

# Branch Context: Diff Against Master

You are helping the user understand all changes in their current branch compared to the master branch. This is similar to Cursor IDE's @Branch feature and GitHub Copilot's "Branch (Diff with Main Branch)" context.

## Your Task

Provide comprehensive context about the branch changes by running these commands in sequence:

### 1. Identify Current Branch and Status
```bash
git branch --show-current
git status --short
```

### 2. Get Branch Statistics
```bash
# Try master first, fall back to main if master doesn't exist
git diff --stat master...HEAD 2>/dev/null || git diff --stat main...HEAD
```

This shows files changed, insertions, and deletions.

### 3. Get Commit History
```bash
git log master..HEAD --oneline --no-decorate 2>/dev/null || git log main..HEAD --oneline --no-decorate
```

This shows all commits in the current branch that aren't in master/main.

### 4. Get File Changes List
```bash
git diff --name-status master...HEAD 2>/dev/null || git diff --name-status main...HEAD
```

This shows which files were modified (M), added (A), deleted (D), or renamed (R).

### 5. Get Full Diff
```bash
git diff master...HEAD 2>/dev/null || git diff main...HEAD
```

This shows the complete code changes.

## How to Present the Information

Structure your response like this:

1. **Branch Overview**: Current branch name and comparison base (master/main)
2. **Summary Statistics**: X files changed, Y insertions, Z deletions
3. **Commit History**: List of commits with messages
4. **Files Changed**: Organized list by change type (Added, Modified, Deleted)
5. **Key Changes**: Highlight the most significant modifications
6. **Patterns & Themes**: Identify what type of work was done (feature, bugfix, refactor, etc.)

## Important Notes

- Always use three-dot syntax `master...HEAD` for proper merge-base comparison
- Handle both `master` and `main` branch names gracefully
- If there are no changes, clearly state the branch is up to date
- Focus on providing context that helps the AI understand the scope and nature of changes
- This context is meant to be consumed by AI to help with code reviews, documentation, or further development

## Example Output Structure

```
📍 Current Branch: feature/user-auth
📊 Comparing with: master

Statistics:
- 8 files changed
- 234 insertions(+)
- 45 deletions(-)

Commits (3):
- abc123 Add login component
- def456 Implement JWT authentication
- ghi789 Add user profile endpoint

Files Changed:
Added:
- src/components/Login.tsx
- src/auth/jwt.ts

Modified:
- src/api/routes.ts
- src/types/user.ts
- README.md

Key Changes:
[Analysis of the most important changes]
```
