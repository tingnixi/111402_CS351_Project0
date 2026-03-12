# Project 0 - Two Sum

The Two Sum problem requires finding two numbers in an array that add up to a specified target value, returning their indices. It can be solved efficiently using a hash map for O(n) time complexity.

## Project Planning

This document outlines the planning for **Project 0 – Two Sum**. The goal is to implement and compare two algorithmic solutions, develop comprehensive tests, and build an automated workflow.

### Objectives
1. Implement two distinct solutions for the Two Sum problem:
   - **TwoSumArray**: brute‑force nested loops (O(n²) time, O(1) space)
   - **TwoSumHashTable**: optimized using a hash table (O(n) time, O(n) space)
2. Write clean, well‑commented code and document complexity.
3. Design and execute thorough unit tests covering normal cases, edge cases (duplicates, negatives), and boundary conditions.
4. Establish CI/CD with GitHub Actions to run tests on every push/pull request.
5. Containerize the project with Docker, including test execution during image build.

### Implementation Steps
1. **Repository setup** – initialize project structure and basic README.
2. **Algorithm development** – code both `TwoSumArray()` and `TwoSumHashTable()` functions in a suitable language (e.g., Python, C++).
3. **Complexity documentation** – add comments or a markdown section explaining time/space trade‑offs.
4. **Unit tests** – create a test suite with coverage for:
   - Standard inputs
   - Duplicate values
   - Negative numbers
   - Minimal and maximal array sizes
5. **CI configuration** – add a GitHub Actions workflow to install dependencies and run the test suite automatically.
6. **Dockerfile creation** – write a Dockerfile that builds the project and executes unit tests as part of the build.

### Testing Strategy
- Use a testing framework (e.g., `unittest`, `pytest` for Python) to structure tests.
- Include assertions for correct index pairs and verify failure modes if assumptions are violated.
- Run tests locally, then verify they pass in the CI pipeline.

### CI/CD and Docker
- Workflow triggers: `push`, `pull_request` events on `main` branch.
- Steps include checkout, set up environment, install dependencies, run tests, and optionally linting.
- Docker build command should execute tests; failure aborts build.

#### Recommended GitHub Actions Workflow

```yaml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build-and-test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Set up language environment
        # adjust to the project's language, e.g., Python, Node, etc.
        uses: actions/setup-python@v4
        with:
          python-version: '3.11'

      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      - name: Run unit tests
        run: |
          # replace with project's test command
          pytest tests/

      - name: Lint code (optional)
        run: |
          # e.g. flake8 or eslint
          flake8 src/

  docker-build:
    needs: build-and-test
    runs-on: ubuntu-latest
    if: github.event_name == 'push' && github.ref == 'refs/heads/main'

    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Build Docker image with tests
        run: |
          docker build --tag twosum:latest .
```

> **Note:** Adjust versions, languages, and commands based on project specifics. The workflow prioritizes testing before dockerization to catch issues early.

### Timeline & Deliverables
- **Week 1**: Algorithm coding & initial tests.
- **Week 2**: Complete test coverage, documentation, and review.
- **Week 3**: Configure CI/CD and Docker, finalize README.

> _This planning section serves both as a guide for development and as documentation for reviewers._

## Development Plan

### Phase 1: Setup
- [ ] Initialize project structure
- [ ] Set up version control and repository
- [ ] Configure development environment

### Phase 2: Implementation
- [ ] Implement TwoSumArray solution
- [ ] Implement TwoSumHashTable solution
- [ ] Add detailed comments and documentation

### Phase 3: Testing
- [ ] Write unit tests for both implementations
- [ ] Test edge cases and boundary conditions
- [ ] Validate correctness of outputs

### Phase 4: CI/CD & Deployment
- [ ] Create GitHub Actions workflow
- [ ] Set up automated testing pipeline
- [ ] Create and test Docker containerization

### Phase 5: Review & Documentation
- [ ] Code review and refinement
- [ ] Finalize complexity analysis
- [ ] Complete project documentation

## Getting Started

```bash
# Clone the repository
git clone <repository-url>

# Navigate to project directory
cd 11402_CS351_Project0

# Install dependencies (if applicable)
# Run tests
# Start development
```