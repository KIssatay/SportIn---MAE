# Contributing to SportIn

Thank you for contributing to SportIn! This document provides guidelines and instructions for contributing to the project.

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Workflow](#development-workflow)
- [Coding Standards](#coding-standards)
- [Commit Guidelines](#commit-guidelines)
- [Pull Request Process](#pull-request-process)
- [Testing Guidelines](#testing-guidelines)

## 🤝 Code of Conduct

- Be respectful and constructive in code reviews
- Help teammates when they face blockers
- Communicate progress and challenges openly
- Follow agreed-upon timelines and deadlines

## 🚀 Getting Started

1. **Set up your development environment**
   - Install Flutter SDK 3.19.0+
   - Install Android Studio or VS Code with Flutter extensions
   - Clone the repository
   - Run `flutter pub get`

2. **Understand the project structure**
   - Read the [README.md](README.md)
   - Familiarize yourself with MVVM architecture
   - Review existing code in your assigned module

3. **Check the Project Board**
   - Visit the GitHub Projects tab
   - Check issues assigned to you
   - Move issues to "In Progress" when you start working

## 🔄 Development Workflow

### 1. Create a Feature Branch

Always create a new branch from `dev`:

```bash
git checkout dev
git pull origin dev
git checkout -b feature/your-feature-name
```

Branch naming conventions:
- `feature/` — new features (e.g., `feature/profile-edit`)
- `fix/` — bug fixes (e.g., `fix/feed-crash`)
- `refactor/` — code improvements (e.g., `refactor/auth-service`)
- `docs/` — documentation (e.g., `docs/api-guide`)

### 2. Make Your Changes

- Follow the [Coding Standards](#coding-standards)
- Write clean, readable code
- Add comments for complex logic
- Keep commits focused and atomic

### 3. Test Your Changes

- Test on both Android and iOS if possible
- Ensure no console errors or warnings
- Check edge cases
- Run `flutter analyze` to check for issues

### 4. Commit Your Changes

Follow the [Commit Guidelines](#commit-guidelines):

```bash
git add .
git commit -m "feat: add profile edit functionality"
```

### 5. Push to Remote

```bash
git push origin feature/your-feature-name
```

### 6. Create a Pull Request

- Go to GitHub and create a PR from your branch to `dev`
- Fill out the PR template completely
- Request review from at least one teammate
- Link related issues using "Closes #123"

### 7. Code Review

- Respond to review comments promptly
- Make requested changes in new commits
- Don't force-push after review has started
- Thank reviewers for their feedback

### 8. Merge

- After approval, merge your PR to `dev`
- Delete your feature branch after merge
- Move related issues to "Done" on Project Board

## 💻 Coding Standards

### Dart Style Guide

Follow the official [Dart Style Guide](https://dart.dev/guides/language/effective-dart/style):

- Use `lowerCamelCase` for variables, functions, parameters
- Use `UpperCamelCase` for classes, enums, typedefs
- Use `lowercase_with_underscores` for file names
- Avoid abbreviations unless widely understood

### Flutter Best Practices

1. **Widget Organization**
   ```dart
   // Good
   class ProfileScreen extends StatefulWidget {
     const ProfileScreen({Key? key}) : super(key: key);
     
     @override
     State<ProfileScreen> createState() => _ProfileScreenState();
   }
   ```

2. **Use const constructors**
   ```dart
   // Good
   const Text('Hello')
   
   // Avoid
   Text('Hello')
   ```

3. **Extract widgets**
   - If a widget tree is >3 levels deep, extract to a separate widget
   - Keep build methods clean and readable

4. **State Management**
   - Use Provider for state management
   - Follow MVVM pattern
   - Keep business logic in ViewModels

### MVVM Architecture

```dart
// Model
class User {
  final String id;
  final String name;
  final String email;
  
  User({required this.id, required this.name, required this.email});
}

// Repository
class UserRepository {
  Future<User> getUser(String id) async {
    // Firestore logic
  }
}

// ViewModel
class ProfileViewModel extends ChangeNotifier {
  final UserRepository _repository;
  User? _user;
  
  User? get user => _user;
  
  Future<void> loadUser(String id) async {
    _user = await _repository.getUser(id);
    notifyListeners();
  }
}

// View
class ProfileScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Consumer<ProfileViewModel>(
      builder: (context, viewModel, child) {
        return Text(viewModel.user?.name ?? '');
      },
    );
  }
}
```

### File Organization

- One class per file
- File name matches class name (lowercase_with_underscores)
- Group related files in folders
- Use barrel files (index.dart) for exports

### Comments

- Use `///` for documentation comments
- Use `//` for inline comments
- Explain *why*, not *what*
- Keep comments updated with code changes

```dart
/// Uploads a file to Firebase Storage and returns the download URL.
/// 
/// Throws [StorageException] if upload fails.
Future<String> uploadFile(File file) async {
  // Use timestamp to ensure unique file names
  final fileName = '${DateTime.now().millisecondsSinceEpoch}_${file.path.split('/').last}';
  // ...
}
```

## 📝 Commit Guidelines

### Commit Message Format

```
<type>: <subject>

<body (optional)>

<footer (optional)>
```

### Types

- `feat:` — new feature
- `fix:` — bug fix
- `docs:` — documentation only
- `style:` — formatting, missing semicolons, etc.
- `refactor:` — code change that neither fixes a bug nor adds a feature
- `test:` — adding or updating tests
- `chore:` — maintenance, dependencies, configuration

### Examples

```
feat: add profile image upload functionality

Implemented profile image upload using Firebase Storage.
Users can now select and upload images from gallery or camera.

Closes #42
```

```
fix: resolve feed infinite scroll duplication

Fixed issue where posts were duplicated when scrolling to bottom.
Added check to prevent loading already-loaded posts.

Fixes #58
```

### Rules

- Use imperative mood ("add" not "added" or "adds")
- Don't capitalize first letter
- No period at the end of subject
- Subject line max 50 characters
- Body lines max 72 characters
- Reference issues in footer

## 🔀 Pull Request Process

### Before Creating PR

- [ ] Code compiles without errors
- [ ] Code passes `flutter analyze`
- [ ] All tests pass
- [ ] New code has appropriate tests
- [ ] Code follows style guidelines
- [ ] Branch is up to date with `dev`

### PR Template

When creating a PR, fill out the template completely:

```markdown
## What does this PR do?
Brief description of changes

## Related Issue
Closes #123

## Type of Change
- [ ] New feature
- [ ] Bug fix
- [ ] Refactoring
- [ ] Documentation

## Testing
- [ ] Tested on Android
- [ ] Tested on iOS
- [ ] Unit tests added/updated
- [ ] Edge cases tested

## Screenshots
(if UI changes)

## Checklist
- [ ] Code follows project structure
- [ ] No console errors or warnings
- [ ] Documentation updated (if needed)
- [ ] Tested edge cases
```

### Code Review Guidelines

**For Authors:**
- Provide context in PR description
- Keep PRs focused and reasonably sized
- Respond to comments within 24 hours
- Be open to feedback

**For Reviewers:**
- Review within 24-48 hours
- Be constructive and specific
- Suggest improvements, don't just criticize
- Approve when satisfied, even if minor suggestions remain

### Review Checklist

- [ ] Code is readable and maintainable
- [ ] Follows MVVM architecture
- [ ] No obvious bugs or logic errors
- [ ] Proper error handling
- [ ] No hardcoded values (use constants)
- [ ] Firebase operations are efficient
- [ ] UI is responsive and matches design
- [ ] No unnecessary dependencies added

## 🧪 Testing Guidelines

### Unit Tests

Write unit tests for:
- ViewModels
- Repositories
- Utility functions
- Business logic

```dart
test('ProfileViewModel loads user data correctly', () async {
  final repository = MockUserRepository();
  final viewModel = ProfileViewModel(repository);
  
  when(repository.getUser('123')).thenAnswer((_) async => User(id: '123', name: 'Test'));
  
  await viewModel.loadUser('123');
  
  expect(viewModel.user?.name, 'Test');
});
```

### Widget Tests

Test critical user flows:
- Login/Signup
- Profile creation/editing
- Post creation
- Message sending

### Integration Tests

Test end-to-end scenarios:
- User onboarding flow
- Creating and viewing posts
- Sending messages

### Running Tests

```bash
# All tests
flutter test

# Specific file
flutter test test/profile_viewmodel_test.dart

# With coverage
flutter test --coverage
```

## 🐛 Reporting Bugs

Use GitHub Issues with the bug template:

**Title**: Clear, descriptive title

**Description**:
- What happened
- What you expected to happen
- Steps to reproduce
- Screenshots (if applicable)
- Device/OS information
- Flutter version

## 💡 Suggesting Features

Use GitHub Issues with the feature request template:

**Title**: Clear feature name

**Description**:
- Problem this solves
- Proposed solution
- Alternative solutions considered
- Additional context

## 📞 Getting Help

- Check existing issues and documentation first
- Ask in team group chat for quick questions
- Create an issue for bugs or feature requests
- Tag relevant team member for module-specific questions

## 🎯 Module Ownership

If you're working outside your assigned module, coordinate with the module owner:

- **Profile/Onboarding**: @Issatay
- **Feed/Search**: @Rafi
- **Auth/Messages**: @Bektay

## ⏰ Response Time Expectations

- PR reviews: within 24-48 hours
- Issue responses: within 24 hours
- Bug fixes: priority-based
- Feature requests: discussed in team meetings

---

Thank you for contributing to SportIn! 🚀