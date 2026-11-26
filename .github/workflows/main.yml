name: Build APK
on: workflow_dispatch
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: unzip -q "$(ls QUREO-Solver*.zip | sort -V | tail -n1)"
      - uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: '17'
      - uses: subosito/flutter-action@v2
        with:
          channel: stable
      - run: bash ci/build.sh
        working-directory: qureo_solver
      - uses: actions/upload-artifact@v4
        with:
          name: qureo-apk
          path: qureo_solver/build/app/outputs/flutter-apk/app-debug.apk
          if-no-files-found: error
