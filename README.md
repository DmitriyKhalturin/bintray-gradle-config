# bintray gradle config

Publish android library to [bintray](https://bintray.com/) (jcenter).

## Setup

### 1. add required plugins to the project's classpath

In you project's `build.gradle`, inside the buildscript -> dependencies add:

```groovy
classpath "com.jfrog.bintray.gradle:gradle-bintray-plugin:{$latest_version}"
classpath "com.github.dcendents:android-maven-gradle-plugin:{$latest_version}"
```

### 2. set your bintray user keys _`locally`_

In your project's `local.properties`:

```groovy
bintray.user={$user_name}
bintray.apikey={$api_key}
bintray.gpg.password={$password}
```

### 3. define the library-specific properties

In your library module's `build.gradle`, add:

```groovy
ext {
  bintrayRepo = "{$repo_name}"
  bintrayName = "{$package_name}"

  publishedGroupId = "{$group_id}"
  artifact = "{$artifact_id}"

  libraryName = "{$library_name}"
  libraryDescription = "{$library_description}"
  libraryVersion = "{$library_version}"

  gitUrl = "{$git_url}"
  siteUrl = "{$site_url}"
  issuesUrl = "{$issues_url}"

  licenseName = "Apache License 2.0"
  licenseUrl = "http://www.apache.org/licenses/LICENSE-2.0.txt"
  allLicenses = ["Apache-2.0"]
}
```

### 4. apply the script

In your library module's `build.gradle`, add:

```groovy
apply from: "https://raw.githubusercontent.com/dmitriykhalturin/bintray-gradle-config/master/bintray.gradle"
```

Or you can copy the `bintray.gradle` file into your library module's root directory, and apply from it by add:

```groovy
apply from: "bintray.gradle"
```

## Publish!

Just run:

```shell
./gradlew clean install bintrayUpload
```

in your project root path.

## Thanks

* [Hong Duan](https://github.com/duanhong169) for DrawableToolbox library and `bintray.gradle`.
