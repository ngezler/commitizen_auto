
# Commitizen Auto Project

This project serves as a guide for understanding and using Commitizen for committing code changes in compliance with Conventional Commits.

## Prerequisites

- Python 3.x
- Git
- Commitizen

## Installation

To install the required packages, run:

```bash
pip install -r requirements.txt
```


## Installation and Configuration Guide

To set up this project locally, follow these steps:

1. Clone the repository:
    ```bash
    git clone https://github.com/ngezler/commitizen_auto.git
    ```

2. Navigate to the project directory:
    ```bash
    cd commitizen_auto
    ```

3. Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```


## Guide: Understanding Commit Types with Commitizen

This guide focuses on making progressive changes to a single Python function, `communicate`, to demonstrate different types of commits in Commitizen.

### Step 1: Initial Function (Starting Point)

The `communicate` function initially looks like this:

```python
def communicate():
    print("Hello Comm!")
```

Commit Message: `chore: add initial communicate function`

### Step 2: Add Functionality (feat)

Next, we'll enhance the function to return a value instead of printing:

```python
def communicate():
    return "Hello Comm!"
```

Commit Message: `feat: modify communicate to return value`

### Step 3: Add Documentation (docs)

Let's add a docstring to our function:

```python
def communicate():
    """
    This function returns a simple greeting.
    """
    return "Hello Comm!"
```

Commit Message: `docs: add docstring to communicate function`

### Step 4: Improve Functionality (refactor)

We'll further improve the function by allowing it to take an argument:

```python
def communicate(message="Hello Comm!"):
    """
    This function returns the provided message.
    """
    return message
```

Commit Message: `refactor: add argument to communicate function`

### Step 5: Breaking Change

Finally, we'll introduce a breaking change by making the argument mandatory:

```python
def communicate(message):
    """
    BREAKING CHANGE: This function now requires a message argument.
    """
    return message
```

Commit Message: `feat: make argument mandatory in communicate function (BREAKING CHANGE)`


## Commit Message Comparisons

### Good Examples

- `chore: add initial communicate function`
- `feat: modify communicate to return value`
- `docs: add docstring to communicate function`
- `refactor: add argument to communicate function`
- `feat: make argument mandatory in communicate function (BREAKING CHANGE)`

### Bad Examples

- `added something to communicate`
- `changes`
- `oops`
- `this might work`
- `empty commit messages`



## Conclusion

Writing good commit messages is crucial for any developer and it's evident in our progressive changes to the `communicate` function. Each commit served not just as a log but also provided context for why the function was changed, whether it was for adding new features, refactoring, or even introducing breaking changes.

By adhering to a set of descriptive conventions, like the ones demonstrated in this guide, you not only make your codebase more understandable but also facilitate effective team collaboration and future decision-making.
