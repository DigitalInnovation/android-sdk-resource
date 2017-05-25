# Android SDK Resource

[Concourse](https://concourse.ci) resource providing Android SDK dependencies.

## Resource type

As a third party resource, this needs to be declared in the pipeline's
`resource_types` section.


## Source Configuration

* `components`: *Required.* An array of strings with the names of components
  required, as they would be given to the `android update sdk` tool.
  `platform-tools` is always implicitely included. e.g.: if you are building
  an APK against SDK 23, and using the Android support library, you might have:

  ```yaml
  components:
    - tools
    - build-tools-25.0.2
    - android-25
    - extra-android-m2repository
  ```

  The order of the components is not important. Duplicates are ignored.


## Behavior

### `check`

No real check is done. The version of the resource is the list of components
that will be provided.

### `in`

Fetches the Android SDK.

> ##### Important note about licenses
> By using this resource, you are automatically accepting the licenses for all
> components specified. Make sure this is acceptable beforehand.

The destination will have the SDK with requested components installed. The
destination directory can be used as the ANDROID_HOME environmental variable
for your task.

Since Concourse caches resource versions, the SDK won't be downloaded again
unless the set of required components changes.

### `out`

This resource does not support this operation. A `put` step in the build plan
will always fail.
