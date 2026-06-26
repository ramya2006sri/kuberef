# Contributing to Kuberef

Thanks for helping improve Kuberef. Contributions should stay focused on the current audit flow, keep the CLI stable, and avoid breaking the existing tests or Docker workflow.

---

## Prerequisites

Before you start, make sure you have:

- Python 3.12+
- Poetry installed
- Access to a Kubernetes cluster to test live Secret validation
- Git installed

---

## Local Setup

```bash
git clone https://github.com/hudazaan/kuberef.git
cd kuberef
poetry install
poetry run pytest
poetry run kuberef path/to/your/k8s-manifest.yaml
```

If you want to test a specific namespace:

```bash
poetry run kuberef path/to/your/k8s-manifest.yaml --namespace production
```

---

## Contribution Workflow

### 1. Fork the Project 

### 2. Clone the Repository 
```bash 
git clone https://github.com/YOURUSERNAME/kuberef.git
cd kuberef
```
### 3. Create your Feature Branch
```bash 
git checkout -b YOUR-BRANCH-NAME
```

### 4. Pick an issue with a clear scope and request assignment before starting work. 

### 5. Make useful changes 
- Edit files as needed 
- Test locally before pushing
- Run tests (`poetry run pytest`)

### 6. Commit your Changes (with Sign off)
```bash 
git add FILESCHANGED 
git commit -m "Brief description of changes" -m "Longer description if needed" --signoff
```

Or use the shorthand:
```bash
git commit -s -m 'your message'
```

### 7. Push to the Branch
```bash 
git push origin YOUR-BRANCH-NAME
``` 

### 8. Open a Pull Request 
- Go to [GitHub](https://github.com) and navigate to the original repository.
- Click "New Pull Request" → select your branch.
- Write a clear PR description (what changed, why, any testing notes).
- Submit the PR.
- Wait for review, approval, and merge.

---

## Pull Request Checklist

- Keep changes focused and small.
- Do not commit secrets or `.env` values.
- Ensure `poetry run pytest` passes.
- The change was tested with a real sample manifest.
- The commit was signed off with git commit -s.
- Any CLI or behavior change was documented in the PR.

--- 

## Getting Started with Issues

Good contributions for this repository usually fall into one of these areas:

- **Beginners:** documentation, tests, small CLI polish, and safer error handling.
- **Intermediate:** parser improvements, manifest discovery, and richer output.
- **Advanced:** new validation modes, Helm-related workflows, and CI integrations.

### Good First Issues

1. **📋 [Create a Minimal PR Template](#1)**  
	Create a standardized .github/pull_request_template.md file to enforce the contribution submission checklist.

2. **✅ [Document Current Secret Patterns](#2)**  
	Document the explicit JSON/YAML structural paths targeted by the Secret extraction engine inside `DOCUMENTATION.md`.

3. **📖 [Add a unit test to parse `test-manifests/`complex-pod.yaml](#3)**  
	Verify extraction of `envFrom`, `volumes`, and `imagePullSecrets` references.

4. **🧪 [Test Multi-Document YAML](#4)**  
	Add a dedicated unit test in `test_parser.py` to verify secret extraction works correctly across multi-document YAML streams.

5. **🎨 [Improve CLI Help Text](#5)**  
	Inject explicit command usage examples for single-file and directory scans into the CLI `--help` terminal output.


### Featured Issues

1. **📊 [Add JSON Output](#6)**  
	Implement a machine-readable JSON output flag for automated CI/CD platform data processing.

2. **🔕 [Add Summary-Only Mode](#7)**  
	Add a `--quiet` / `-q` flag to suppress individual file tables and provide summary-only mode for cleaner pipeline logs.

3. **♿ [Handle Invalid YAML Gracefully](#8)**  
	Catch `yaml.YAMLError` in the file parsing loop to gracefully warn and skip invalid files, and add an integration test for it.

4. **🛣️ [Add Recursive Manifest Scanning](#9)**  
	Update the directory processing engine to recursively scan nested sub-folders for YAML manifests.

### Advanced Issues

1. **🧩 [Add ConfigMap Validation](#10)**  
	Use the same recursive discovery approach and live API validator to support ConfigMap reference and key-level verification.

2. **🚢 [Add Helm Template Support](#11)**  
	Integrate programmatic support to auto-render Helm charts using `helm template` before auditing references. 

3. **📝 [Add SARIF or GitHub Annotations](#12)**  
	Add a CI-mode flag to emit GitHub workflow execution annotations or a SARIF log matrix for seamless PR integration.

4. **⚙️ [Add a Manifest Preprocessor](#13)**  
	Refactor the discovery loop with a Manifest Preprocessor layer to dynamically extract inner Pod specs from any advanced or custom Kubernetes workload type.

5. **🔌 [Add a kubectl Plugin Wrapper](#14)**  
	Configure a plugin wrapper distribution to allow Kuberef to be executed natively as a `kubectl ref` extension subcommand for teams that prefer kubectl integration.

### Debugging 

If you find an issue or a bug, include:

- The manifest or a minimal reproduction.
- The command you ran.
- The expected result.
- The actual result.

That makes it much easier to confirm and fix issues quickly.

--- 


All the best, and thanks for contributing to Kuberef. 🤝✨



