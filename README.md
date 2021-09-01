# action-install-flutter

This action installs [Flutter](https://flutter.dev) so your workflow can run 
Flutter commands like `flutter test`.

# Inputs

## `version`

By default, the `stable` channel is installed however any Flutter branch or 
version tag can be set e.g., `2.2.3`, `master`, `beta`, `dev`.

We recommend using a fixed version rather than a channel as it allows you to 
checkout an old commit and run an action with the version of Flutter used at the
time of the commit.

# Example

```yaml
name: Flutter Workflow
env:
  FLUTTER_VERSION: "2.2.3"
on: push
jobs:
  test:
    name: Run Tests
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Install Flutter
        uses: britannio/action-install-flutter@v1
        with:
          version: $FLUTTER_VERSION
      - name: Get Packages
        run: flutter pub get
      - name: Run Tests
        run: flutter test --no-pub
```