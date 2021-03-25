# action-install-flutter

Installs [Flutter](https://flutter.dev)


## Versioning

If no version is specified then the stable channel is used.

You can either select one of the flutter channels: `master`, `dev`, `beta`, `stable` or you can select specific version like `1.22.6`.



## Example

```yaml
name: Flutter Workflow
env:
  FLUTTER_VERSION: "stable"
on: push
jobs:
  test:
    name: Run Tests
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Installing Flutter
        uses: britannio/action-install-flutter@v1.0
        with:
          version: $FLUTTER_VERSION
      - name: Installing dependencies
        run: flutter pub get
      - name: Running tests
        run: flutter test --no-pub
```