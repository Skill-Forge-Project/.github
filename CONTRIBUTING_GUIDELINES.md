# Code Standards and Contribution Convention

## 1. 📂 Repository Structure
- Maintain a clear and modular folder structure.
- Group related features and services logically.
- Keep documentation files (e.g. README.md, CONTRIBUTING.md, docs/) up to date

## 2. 🧾 Commit Message Format
Use the following format for all commit messages:

```sh
<type>(scope): <description>

[optional body]

[optional footer(s)]


### Example Commit Msg
feat(auth): implement password reset functionality

Added API endpoint `/auth/reset-password` and integrated frontend form with email verification.
Includes input validation, error handling, and success alerts.

Closes #72

```

### Types:
- feat: New feature
- fix: Bug fix
- docs: Documentation changes
- style: Code style (formatting, semi-colons, etc.)
- refactor: Code restructuring without behavior changes
- test: Adding/modifying tests
- chore: Miscellaneous tasks

## 3. 📤 Pull Request Guidelines
- PRs should be small, focused, and solve one problem at a time.
- Always link relevant issue numbers with Closes #123.
- Include a short, clear title and description.
- Add screenshots for UI/UX changes.
- Request reviews from relevant team members and assign appropriate tags (e.g. needs-review, bug, feature, - etc.).
- Ensure successful CI checks before requesting a merge.

> By default, when creating a PR, a pre-defined template will be loaded. Follow the template convention to ensure all necessary information is provided.

## 4. 🧪 Testing
- Write unit and integration tests for all new logic(when applicable & higly recommended).
- Tests should live beside the files they test, in a __tests__ directory or with .test suffix.
- Use meaningful test descriptions and cover edge cases.

## 5. 🧹 Code Style
- Follow the specific programming language or framework convention or adopt Prettier/ESLint/Black/Flake8, etc., based on the tech stack.
- Configure auto-formatting in IDEs via .editorconfig and linter configs.
- Avoid commented-out code unless temporarily needed with a `TODO: and username/note.`
- Add comments for complex logic, but avoid **obvious** comments.
- Prefer self-explanatory variable and function names.
- For complex logic, add concise inline or block comments.

> Example for commented-out code:
```py
# Get all quests filtered by language
@quests_bp.route('/quests/<language>', methods=['GET'])
@token_required
def get_quests_by_language(language):
    """Get all quests filtered by language.

    Args:
        language (str): Programming language

    Returns:
        JSON: List of quests filtered by language
    """

    try:
        result = db.session.execute(text("SELECT * FROM coding_quests WHERE language = :language"), {"language": language})
        quests = [dict(row._mapping) for row in result.fetchall()]
        return jsonify(quests)
    except Exception as e:
        return jsonify({"error": str(e)}), 500
```

## 7. 📥 Issue Guidelines
- Title: Be specific: “Fix broken modal on login page” > “UI not working”
- Description: Steps to reproduce, expected/actual results, screenshots/logs, and proposed fix if known.
- Use labels (bug, enhancement, question, etc.) and assign it to appropriate milestones and people.
- By default, when opening an issue, a pre-defined template will be loaded. Follow the template convention to ensure all necessary information is provided.
- If the issue is a feature request, include user stories and acceptance criteria.
- If issue is assigned to you, provide regular updates on progress and expected resolution time.
- If you are unable to resolve the issue, provide a clear explanation of the challenges faced and any potential next steps.If needed reassign the issue to another team member and add a comment explaining the reassignment.

## 8. 🚦Branch Naming
- Use descriptive names that reflect the purpose of the branch.
- Use the following format:
  - `feature/short-description` for new features
  - `bugfix/short-description` for bug fixes
  - `hotfix/short-description` for urgent fixes
  - `refactor/short-description` for code refactoring
  - `test/short-description` for test-related changes
  - `docs/short-description` for documentation updates
  - `release/vX.Y.Z` for version releases
  - `chore/short-description` for maintenance & other miscellaneous tasks

> Example:
```sh
git checkout -b feature/add-user-authentication # Create new feature branch
git checkout -b bugfix/fix-login-error # Create new bug fix branch
git checkout -b hotfix/urgent-fix # Create new hotfix branch
```

## 9. 🔄 Merging
- Use `squash and merge` for clean history unless otherwise specified.
- Resolve all merge conflicts before requesting a review.

## 10. 📚 Documentation
- Keep all documentation up to date with code changes.
- Use Markdown for README, CONTRIBUTING, and other documentation files.
- Document all public APIs, including endpoints, request/response formats, and error codes.
- Use comments in code to explain complex logic or important decisions.
- Add examples and usage instructions in the documentation.



