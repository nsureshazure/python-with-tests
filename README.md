# Python Project with Tests 

## Writing and Running Unit Tests

### Writing Unit Tests

- All unit tests are located in the `tests/` directory.
- Test files should be named with the pattern `test_*.py`.
- Each test function should start with `def test_...`.
- Example:
  ```python
  def test_my_function():
      assert my_function(2) == 4
  ```

### Running Unit Tests Locally

1. **Install dependencies** (preferably in a virtual environment):
   ```sh
   pip install -r requirements.txt
   pip install .
   pip install pytest coverage
   ```
2. **Run all tests:**
   ```sh
   pytest
   ```
3. **Run tests with coverage:**
   ```sh
   coverage run -m pytest
   coverage report
   ```

### Generating Coverage Report

- To generate a coverage XML file (required for SonarQube/SonarCloud):
  ```sh
  coverage run -m pytest
  coverage xml
  ```
- This will create a `coverage.xml` file in the project root.

---

## How Coverage is Used in CI/CD

### GitHub Actions Workflow

- On every push or pull request, GitHub Actions will:
  1. Install dependencies.
  2. Run tests with coverage:
     ```sh
     coverage run -m pytest
     coverage xml
     ```
  3. Cache the `.coverage` and `coverage.xml` files.
  4. On the main branch, the workflow restores the coverage files and runs the SonarQube scan.

- The SonarQube/SonarCloud GitHub Action automatically picks up the `coverage.xml` file and uses it to report code coverage in the Sonar dashboard.

**You do not need to manually upload coverage files—this is handled by the workflow.**

---

Original repo here - https://github.com/Mastercard/client-encryption-python
License is MIT License, as of 18th August 2025
