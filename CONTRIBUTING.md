# Contributing to Adventure Game

Thank you for considering contributing to Adventure Game! We welcome contributions from everyone. By participating in this project, you agree to abide by our [Code of Conduct](./docs/CODE_OF_CONDUCT).

## How to Contribute

1. **Fork the repository**: Click the "Fork" button at the top right of the repository page to create a copy of the repository in your GitHub account.

2. **Clone your fork**: Clone your forked repository to your local machine.

    ```sh
    git clone https://github.com/pavel-hrdina/AdventureGame
    cd AdventureGame
    ```

3. **Create a branch**: Create a new branch for your changes.

    ```sh
    git checkout -b feature-branch
    ```

4. **Make your changes**: Make your changes to the codebase. Ensure your code follows the project's coding standards and includes appropriate tests.

5. **Commit your changes**: Commit your changes with a clear and descriptive commit message.

    ```sh
    git commit -am 'Add new feature'
    ```

6. **Push to your fork**: Push your changes to your forked repository.

    ```sh
    git push origin feature-branch
    ```

7. **Create a Pull Request**: Go to the original repository and create a pull request from your forked repository. Provide a clear and descriptive title and description for your pull request.

## Code Style

Please follow the coding style used in the project. Ensure your code is properly formatted and includes comments where necessary.

## Running Tests

Before submitting your changes, run the tests to ensure everything is working correctly.

```sh
./gradlew test
```

Tests are also run automatically on every push to the repository. If the tests fail, your changes will not be merged.
