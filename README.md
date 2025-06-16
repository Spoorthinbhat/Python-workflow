# Python Reusable GitHub Actions Workflow

A flexible and robust **reusable workflow** to **test and build Python projects** using `pip`, `poetry`, `pipenv`, or `uv`.

---

## 🚀 How to Use

In your GitHub workflow, call this reusable workflow:

```yaml
jobs:
  build:
    uses: your-org/your-repo/.github/workflows/python-reusable.yml@main
    with:
      python-version: '3.12'
      build-tool: 'poetry'
```

---

## 🔧 Inputs

| Name             | Type   | Description                                           | Required | Example    |
|------------------|--------|-------------------------------------------------------|----------|------------|
| `python-version` | string | Python version to set up                              | ✅ Yes   | `"3.12"`   |
| `build-tool`     | string | Build tool to use: `pip`, `poetry`, `pipenv`, or `uv` | ✅ Yes   | `"poetry"` |

---

## 📁 Project Requirements

Your project **must** include at least one of the following (based on the selected build tool):

- `requirements.txt` — for `pip`, `uv`
- `pyproject.toml` — for `poetry`
- `Pipfile` — for `pipenv`

> 🛑 If the required file is not found, the workflow will fail with a clear error message.

Additionally:

- `pytest` should be listed as a dependency.
- Tests should be located in a `tests/` directory.

---

## 📦 Example Project Structure

```
.
├── pyproject.toml
├── requirements.txt
├── Pipfile
├── tests/
│   ├── test_example.py
│   └── ...
```

---

## ⚡ Dependency Caching

To speed up workflow runs, dependencies are cached:

| Build Tool | Cache Location      |
|------------|---------------------|
| `pip`      | `~/.cache/pip`      |
| `poetry`   | `~/.cache/pypoetry` |
| `pipenv`   | `~/.cache/pipenv`   |
| `uv`       | `~/.cache/uv`       |

---

## 📊 Workflow Summary

At the end of each run, a summary shows the status of:

- ✅ Checkout  
- 🐍 Python Setup  
- 📥 Input Validation  
- 💾 Cache  
- 📦 Dependency Installation  
- 🧪 Test Execution

---

## 📝 Notes

- Automatically installs the selected build tool if it's not already available.
- For `uv`, a `.venv/` is created if one doesn't exist.

---

Feel free to fork, contribute, or adapt this for your team's needs!
