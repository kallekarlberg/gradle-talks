# The new stuff…

## Clickable report URLs

Whenever a task that produces some kind of report fails, you get a URL to the report file.

This makes it much easier to open.

* Linux - directly clickable (most terminals)
* Mac OS - ⌘ + click to open
* Windows - copy/paste

Small feature, surprisingly useful.

## Upgrade Assistance

Gradle has a frequent release cycle, we want to help you keep current.

The “build comparison” support facilitates _testing_ your build with different versions.

Verify that your _outputs_ are the same with the new Gradle version.

--- 

FUTURE: Build Migration

## Maven conversion

* Convert a `pom.xml` to a `build.gradle`
* Gives you a staring point
* Incubating!

--- 

FUTURE: Maven import

## Test Output

* Detailed test information, in the console
* Stacktraces
* Events (e.g. skipped)
* Tunable and flexible
* Multiple logging levels

There's a [very detailed forum post](http://forums.gradle.org/gradle/topics/whats_new_in_gradle_1_1_test_logging) on this.

## New dependency report

* Indicates both *requested* and *selected* versions
* Much better insight into version conflicts

(previous version only showed *selected*)

## Dependency Insight

* Inverse of `dependencies` report
* Shows path **to** a dependency
* Explains how/why a dependency is in the graph

## Dependency resolution API

* `ResolutionResult`
* A model of the resolved dependency graph
* *requested* and *selected*
* Selection *reason*
* Basis for new dependency reports
* Fine grained conflict handling rules 

# Performance & Memory

Relevance depends on scenarios

---

A lot of potential

Step-by-step improvements

Spend a lot of effort to measure (dedicated performance machines)

Many different aspects (responsiveness (what tasks, dependencies, debugging), average build time, clean build time, configuration time)

Means: Avoidance, Profiling & Low level optimisation, apply more resources

## Parallel execution

* --parallel 
* --parallel-threads=«num»
* Incubating!

---

This is not a stable feature, and has structural requirements.

# Compiler Daemons

For Java, Groovy, Scala

---

Compile processes = submodules * 2

Should be forked (leaks, clean classpath, health checks)

Groovy is always forked.

Particularly relevant if warm up phase is expensive

# Incremental Scala Compile

Zinc (SBT) integration

---

Scala first class platform 
Cooperation with Typesafe

# Native integration

A platform wonderland

---

* Works with Java 5
* dynamic console output
* native client
* local/remote filesystem
* permissions
* keystores
* proxy settings
* events
* native client
* dog food for Gradle C++/JNI support.

## Continue on failure

Live Demo

## Android

    apply plugin: 'android'

    version = '1.0'

    android {
      target 'android-16'
      productFlavors {
        free { packageName = 'org.gradle.sample.free' }
        paid
      }
      buildTypes { custom }
    }

    sourceSets {
      main.java.srcDir 'some-dir'
      main.resources.srcDir 'some-resources'
      free.java.srcDir 'some-free-dir'
    }
