### How to check test coverage?
  - We can use command to generate code coverage report
    ng test --no-watch --code-coverage

    a coverage/ folder will be created in your project directory.
    Open coverage/index.html in a browser to see a detailed graphical report showing which files and lines are covered by tests.

    The CLI also outputs a summary of coverage percentages for statements, branches, functions, and lines.
  - Enable Code Coverage by Default
    In your angular.json file, add or update the test options:
      "test": {
        "options": {
          "codeCoverage": true
        }
      }

