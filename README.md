# DraftResolve

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

DraftResolve is a powerful tool for comparing, merging, and resolving conflicts in document drafts and versions. Whether you're a writer managing multiple revisions, a developer handling documentation, or a team collaborating on shared documents, DraftResolve simplifies the process of maintaining document consistency.

## Features

- **Smart Conflict Detection**: Automatically identify conflicts and differences between document versions
- **Inconsistency Resolution**: Detect and fix style, terminology, and formatting inconsistencies within documents
- **Multiple Format Support**: Works with Markdown, HTML, plaintext, and Word documents
- **Version Merging**: Intelligently merge changes from multiple document versions
- **Command-line Interface**: Easy to use in scripts and automation workflows
- **Python API**: Integrate with your existing Python applications
- **Web Interface**: Browser-based UI for visual comparison and conflict resolution

## System Architecture

DraftResolve consists of three main components:

### Frontend

The frontend provides a user-friendly web interface for:
- Uploading and comparing documents
- Visualizing differences between versions
- Interactive conflict resolution
- Document history management
- User authentication and project management

Technologies: React, TypeScript, Tailwind CSS

### Backend

The backend powers the core functionality:
- Document parsing and standardization
- Intelligent diff algorithms
- Content analysis and inconsistency detection
- Resolution strategies
- Document storage and retrieval

Technologies: Python, FastAPI, SQLAlchemy

### API

The REST API enables integration with other tools and services:
- Document upload and retrieval
- Comparison operations
- Conflict resolution
- Batch processing
- Authentication and access control

## Installation

### Using pip (Python Package)

```bash
pip install draftresolve
```

### For Development

```bash
# Clone the repository
git clone https://github.com/yourusername/draftresolve.git
cd draftresolve

# Install dependencies
pip install -e ".[dev]"
```

## Quick Start

### Command Line Interface

```bash
# Compare two versions of a document
draftresolve compare old.md new.md

# Check a document for internal inconsistencies
draftresolve check document.md

# Resolve conflicts and output a merged document
draftresolve resolve version1.md version2.md --output merged.md
```

### Python API

```python
from draftresolve import Resolver

# Initialize resolver
resolver = Resolver()

# Compare documents
conflicts = resolver.compare("old_version.md", "new_version.md")

# Print conflicts
for conflict in conflicts:
    print(f"Conflict at line {conflict.line_number}: {conflict.description}")
    print(f"Version 1: {conflict.version1_text}")
    print(f"Version 2: {conflict.version2_text}")
    print(f"Suggested resolution: {conflict.suggested_resolution}")
```

### Web Interface

```bash
# Start the web server
draftresolve server --port 8000
```

Then navigate to `http://localhost:8000` in your browser.

## API Endpoints

The REST API provides the following main endpoints:

- `POST /api/documents` - Upload a document
- `GET /api/documents/{doc_id}` - Retrieve a document
- `POST /api/comparison` - Compare two documents
- `GET /api/comparison/{comparison_id}` - Get comparison results
- `POST /api/resolve` - Resolve conflicts between documents
- `GET /api/projects` - List projects (authenticated)
- `POST /api/projects` - Create a new project (authenticated)

For full API documentation, start the server and navigate to `http://localhost:8000/docs`.

## Configuration

DraftResolve can be configured via:

1. Command-line arguments
2. Environment variables
3. Configuration file

Example configuration file (`draftresolve.yaml`):

```yaml
storage:
  type: local
  path: ./documents

server:
  host: 0.0.0.0
  port: 8000
  workers: 4

auth:
  enabled: true
  jwt_secret: your-secret-key
  token_expiry: 86400  # 24 hours

resolution:
  default_strategy: smart
  conflict_threshold: 0.7
```

## Contributing

Contributions are welcome! Please check out our [Contributing Guide](CONTRIBUTING.md) for details on how to get started.

### Development Setup

```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install development dependencies
pip install -e ".[dev]"

# Run tests
pytest
```
