# Android SDK Resource

[Concourse](https://concourse.ci) resource providing Android SDK dependencies.

## Resource type

As a third party resource, this needs to be declared in the pipeline's
`resource_types` section.


## Source Configuration

* `components`: *Required.* An array of strings with the names of components
  required, as they would be given to the `android update sdk` tool.
  `platform-tools` is always implicitly included. e.g.: if you are building
  an APK against SDK 23, and using the Android support library, you might have:

  ```yaml
  components:
    - tools
    - build-tools-25.0.3
    - android-25
    - extra-android-m2repository
  ```

  The order of the components is not important. Duplicates are ignored.
