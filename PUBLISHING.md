# Publishing

This package is published to **AWS CodeArtifact** (`d4capital` / `python-internal`) via GitHub Actions.

## Tag Format

```
v<version>
```

### Examples

```bash
git tag v0.9.0
git tag v0.9.1a1
```

## How to Publish

1. **Bump the version** in `neuraxle/__init__.py` (`__version__`)
2. **Commit and push** to the branch
3. **Tag and push** the tag:

```bash
git tag v<version>
git push origin v<version>
```

The workflow (`.github/workflows/publish-package.yml`) will:
- Parse the version from the tag
- Override `__version__` in `neuraxle/__init__.py` to match the tag
- Build the package (sdist + wheel)
- Upload to CodeArtifact via `twine`

## Versioning Scheme

Versions follow [Semantic Versioning](https://semver.org/):

- **Major** (`1.0.0`): Breaking changes — any change to existing public interfaces, removed functionality, or incompatible behaviour
- **Minor** (`0.10.0`): New features — backwards-compatible additions (new functions, optional parameters, etc.)
- **Patch** (`0.9.1`): Bug fixes — backwards-compatible fixes with no new functionality

Pre-release versions:

- **Alpha**: `0.9.0a1`
- **Release candidate**: `0.9.0rc1`

The tag is the source of truth for the published version.

## CodeArtifact Details

| Field | Value |
|---|---|
| Domain | `d4capital` |
| Repository | `python-internal` |
| Account | `152192834757` (dev) |
| Region | `us-east-2` |
| Auth | OIDC via `github-codeartifact-publish-dev` role |
