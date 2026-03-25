# Reproduction Repo for Gradle '!!' version notation
Gradle supports describing `strictly` and `preferred` version constraints using a shorthand.
The behavior briefly explained in the [documentation](https://docs.gradle.org/current/userguide/dependency_versions.html#sec:rich-version-constraints).
```kotlin
implementation("org.slf4j:slf4j-api:[1.7, 1.8[!!1.7.25")
// is equivalent to
implementation("org.slf4j:slf4j-api") {
    version {
        strictly("[1.7, 1.8[")
        prefer("1.7.25")
    }
}
```

## Current behavior

Renovate doesn't understand the dependency and ignores it entirely

## Expected behavior

The base range is updated as expected with the `bump` strategy and the preferred version is increased as well

## Link to the Renovate issue or Discussion
[Link to the Renovate Discussion here.](https://github.com/renovatebot/renovate/discussions/24781) \
[Link to the Pull Request here](https://github.com/renovatebot/renovate/pull/33453)
