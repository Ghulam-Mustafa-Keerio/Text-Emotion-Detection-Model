# Contributing to Text Emotion Detection Model

Thank you for your interest in contributing to the Text Emotion Detection Model project! We welcome contributions from the community and are grateful for your support.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
  - [Reporting Bugs](#reporting-bugs)
  - [Suggesting Enhancements](#suggesting-enhancements)
  - [Pull Requests](#pull-requests)
- [Development Setup](#development-setup)
- [Style Guidelines](#style-guidelines)
- [Commit Message Guidelines](#commit-message-guidelines)

## Code of Conduct

This project and everyone participating in it is governed by our [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to the project maintainers.

## How Can I Contribute?

### Reporting Bugs

Before creating bug reports, please check the existing issues to avoid duplicates. When creating a bug report, include as many details as possible:

**Bug Report Template:**
- **Description**: A clear and concise description of the bug
- **Steps to Reproduce**: Detailed steps to reproduce the behavior
- **Expected Behavior**: What you expected to happen
- **Actual Behavior**: What actually happened
- **Environment**: 
  - OS: [e.g., Windows 10, macOS 12, Ubuntu 20.04]
  - Python Version: [e.g., 3.8.10]
  - Dependencies: Version numbers of relevant packages
- **Screenshots**: If applicable, add screenshots
- **Additional Context**: Any other relevant information

### Suggesting Enhancements

We welcome suggestions for enhancements! Please provide:

- **Clear Use Case**: Describe the problem you're trying to solve
- **Proposed Solution**: Your suggested approach to solving it
- **Alternatives Considered**: Other solutions you've thought about
- **Benefits**: How this enhancement helps users

### Pull Requests

1. **Fork the Repository**
   ```bash
   git clone https://github.com/YOUR-USERNAME/Text-Emotion-Detection-Model.git
   cd Text-Emotion-Detection-Model
   ```

2. **Create a Branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```
   
   Use descriptive branch names:
   - `feature/` for new features
   - `bugfix/` for bug fixes
   - `docs/` for documentation changes
   - `refactor/` for code refactoring

3. **Make Your Changes**
   - Write clear, concise code
   - Follow the project's coding style
   - Add comments where necessary
   - Update documentation if needed

4. **Test Your Changes**
   - Ensure all existing tests pass
   - Add new tests for your changes
   - Test on multiple Python versions if possible

5. **Commit Your Changes**
   ```bash
   git add .
   git commit -m "Add descriptive commit message"
   ```

6. **Push to Your Fork**
   ```bash
   git push origin feature/your-feature-name
   ```

7. **Submit a Pull Request**
   - Go to the original repository
   - Click "New Pull Request"
   - Select your branch
   - Fill in the PR template with:
     - Description of changes
     - Related issue number (if applicable)
     - Testing performed
     - Screenshots (if UI changes)

## Development Setup

### Prerequisites
- Python 3.8 or higher
- pip package manager
- Git

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/Ghulam-Mustafa-Keerio/Text-Emotion-Detection-Model.git
   cd Text-Emotion-Detection-Model
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Download NLTK data (if needed)**
   ```bash
   python -m nltk.downloader punkt stopwords
   ```

5. **Run Jupyter Notebook**
   ```bash
   jupyter notebook
   ```

## Style Guidelines

### Python Code Style

- Follow [PEP 8](https://www.python.org/dev/peps/pep-0008/) style guidelines
- Use 4 spaces for indentation (no tabs)
- Maximum line length: 100 characters
- Use descriptive variable and function names

**Example:**
```python
# Good
def predict_emotion(text):
    """Predict emotion from input text."""
    text_vectorized = vectorizer.transform([text])
    return model.predict(text_vectorized)

# Avoid
def pred(t):
    tv = vec.transform([t])
    return m.predict(tv)
```

### Documentation

- Add docstrings to all functions and classes
- Use clear, concise language
- Include examples where helpful
- Keep README.md updated with new features

### Jupyter Notebooks

- Clear all outputs before committing
- Use markdown cells to explain your approach
- Keep code cells focused and modular
- Add visualizations where appropriate

## Commit Message Guidelines

Write clear, meaningful commit messages following this format:

```
<type>: <subject>

<body>

<footer>
```

### Type
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

### Examples

```
feat: Add multi-language emotion detection support

Implemented translation layer to support Spanish and French 
emotion detection using Google Translate API.

Closes #123
```

```
fix: Correct precision calculation in evaluation metrics

Fixed division by zero error when calculating precision 
for classes with no predicted samples.

Fixes #456
```

## Testing

Before submitting a PR, ensure:

1. All existing tests pass
2. New features have accompanying tests
3. Code coverage doesn't decrease
4. Manual testing has been performed

## Questions?

If you have questions or need help:
- Open an issue with the "question" label
- Reach out to the maintainers
- Check existing documentation and issues first

## Recognition

Contributors will be recognized in:
- Project README
- Release notes
- GitHub contributors page

Thank you for contributing to make emotion detection more accessible and accurate! 🎉
