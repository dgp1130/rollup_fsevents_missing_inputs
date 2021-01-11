# `@bazel/rollup` v3 optional dependency

This is a simple reproduction which uses `rollup_bundle()` to build a trivial
JavaScript bundle. However, it fails on Linux platforms because `fsevents`
cannot be installed.

```
$ rm -rf node_modules/ && bazel clean && npm install && bazel test //... 
INFO: Invocation ID: 7d032ea0-ca2d-42f9-af90-76da8f3248cd
INFO: Starting clean (this may take a while). Consider using --async if the clean takes more than several minutes.

> @bazel/rollup@3.0.0 postinstall /home/dparker/Source/rollup_v3/node_modules/@bazel/rollup
> node npm_version_check.js

npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@2.1.3 (node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.1.3: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})

added 5 packages from 23 contributors and audited 6 packages in 1.958s
found 0 vulnerabilities

INFO: Invocation ID: 3db8d9d5-edc0-4ec4-a29d-4de4bac578ed
INFO: Analyzed target //:bundle (30 packages loaded, 129 targets configured).
INFO: Found 1 target and 0 test targets...
ERROR: /home/dparker/.cache/bazel/_bazel_dparker/d162027e785a52b12612ed75680640a1/external/npm/rollup/bin/BUILD.bazel:9:14: Couldn't build runfiles for @npm//rollup/bin:rollup: @npm//rollup/bin:rollup: missing input file 'external/npm/node_modules/fsevents/LICENSE', owner: '@npm//:node_modules/fsevents/LICENSE'
ERROR: /home/dparker/.cache/bazel/_bazel_dparker/d162027e785a52b12612ed75680640a1/external/npm/rollup/bin/BUILD.bazel:9:14: Couldn't build runfiles for @npm//rollup/bin:rollup: @npm//rollup/bin:rollup: missing input file 'external/npm/node_modules/fsevents/README.md', owner: '@npm//:node_modules/fsevents/README.md'
ERROR: /home/dparker/.cache/bazel/_bazel_dparker/d162027e785a52b12612ed75680640a1/external/npm/rollup/bin/BUILD.bazel:9:14: Couldn't build runfiles for @npm//rollup/bin:rollup: @npm//rollup/bin:rollup: missing input file 'external/npm/node_modules/fsevents/fsevents.d.ts', owner: '@npm//:node_modules/fsevents/fsevents.d.ts'
ERROR: /home/dparker/.cache/bazel/_bazel_dparker/d162027e785a52b12612ed75680640a1/external/npm/rollup/bin/BUILD.bazel:9:14: Couldn't build runfiles for @npm//rollup/bin:rollup: @npm//rollup/bin:rollup: missing input file 'external/npm/node_modules/fsevents/fsevents.js', owner: '@npm//:node_modules/fsevents/fsevents.js'
ERROR: /home/dparker/.cache/bazel/_bazel_dparker/d162027e785a52b12612ed75680640a1/external/npm/rollup/bin/BUILD.bazel:9:14: Couldn't build runfiles for @npm//rollup/bin:rollup: @npm//rollup/bin:rollup: missing input file 'external/npm/node_modules/fsevents/fsevents.node', owner: '@npm//:node_modules/fsevents/fsevents.node'
ERROR: /home/dparker/.cache/bazel/_bazel_dparker/d162027e785a52b12612ed75680640a1/external/npm/rollup/bin/BUILD.bazel:9:14: Couldn't build runfiles for @npm//rollup/bin:rollup: @npm//rollup/bin:rollup: missing input file 'external/npm/node_modules/fsevents/package.json', owner: '@npm//:node_modules/fsevents/package.json'
ERROR: /home/dparker/.cache/bazel/_bazel_dparker/d162027e785a52b12612ed75680640a1/external/npm/rollup/bin/BUILD.bazel:9:14: Couldn't build runfiles for @npm//rollup/bin:rollup: @npm//rollup/bin:rollup: missing input file 'external/npm/node_modules/fsevents/LICENSE', owner: '@npm//:node_modules/fsevents/LICENSE'
ERROR: /home/dparker/.cache/bazel/_bazel_dparker/d162027e785a52b12612ed75680640a1/external/npm/rollup/bin/BUILD.bazel:9:14: Couldn't build runfiles for @npm//rollup/bin:rollup: @npm//rollup/bin:rollup: missing input file 'external/npm/node_modules/fsevents/README.md', owner: '@npm//:node_modules/fsevents/README.md'
ERROR: /home/dparker/.cache/bazel/_bazel_dparker/d162027e785a52b12612ed75680640a1/external/npm/rollup/bin/BUILD.bazel:9:14: Couldn't build runfiles for @npm//rollup/bin:rollup: @npm//rollup/bin:rollup: missing input file 'external/npm/node_modules/fsevents/fsevents.d.ts', owner: '@npm//:node_modules/fsevents/fsevents.d.ts'
ERROR: /home/dparker/.cache/bazel/_bazel_dparker/d162027e785a52b12612ed75680640a1/external/npm/rollup/bin/BUILD.bazel:9:14: Couldn't build runfiles for @npm//rollup/bin:rollup: @npm//rollup/bin:rollup: missing input file 'external/npm/node_modules/fsevents/fsevents.js', owner: '@npm//:node_modules/fsevents/fsevents.js'
ERROR: /home/dparker/.cache/bazel/_bazel_dparker/d162027e785a52b12612ed75680640a1/external/npm/rollup/bin/BUILD.bazel:9:14: Couldn't build runfiles for @npm//rollup/bin:rollup: @npm//rollup/bin:rollup: missing input file 'external/npm/node_modules/fsevents/fsevents.node', owner: '@npm//:node_modules/fsevents/fsevents.node'
ERROR: /home/dparker/.cache/bazel/_bazel_dparker/d162027e785a52b12612ed75680640a1/external/npm/rollup/bin/BUILD.bazel:9:14: Couldn't build runfiles for @npm//rollup/bin:rollup: @npm//rollup/bin:rollup: missing input file 'external/npm/node_modules/fsevents/package.json', owner: '@npm//:node_modules/fsevents/package.json'
ERROR: /home/dparker/Source/rollup_v3/BUILD.bazel:3:14: Couldn't build file bundle.js: //:bundle: missing input file 'external/npm/node_modules/fsevents/LICENSE', owner: '@npm//:node_modules/fsevents/LICENSE'
ERROR: /home/dparker/Source/rollup_v3/BUILD.bazel:3:14: Couldn't build file bundle.js: //:bundle: missing input file 'external/npm/node_modules/fsevents/README.md', owner: '@npm//:node_modules/fsevents/README.md'
ERROR: /home/dparker/Source/rollup_v3/BUILD.bazel:3:14: Couldn't build file bundle.js: //:bundle: missing input file 'external/npm/node_modules/fsevents/fsevents.d.ts', owner: '@npm//:node_modules/fsevents/fsevents.d.ts'
ERROR: /home/dparker/Source/rollup_v3/BUILD.bazel:3:14: Couldn't build file bundle.js: //:bundle: missing input file 'external/npm/node_modules/fsevents/fsevents.js', owner: '@npm//:node_modules/fsevents/fsevents.js'
ERROR: /home/dparker/Source/rollup_v3/BUILD.bazel:3:14: Couldn't build file bundle.js: //:bundle: missing input file 'external/npm/node_modules/fsevents/fsevents.node', owner: '@npm//:node_modules/fsevents/fsevents.node'
ERROR: /home/dparker/Source/rollup_v3/BUILD.bazel:3:14: Couldn't build file bundle.js: //:bundle: missing input file 'external/npm/node_modules/fsevents/package.json', owner: '@npm//:node_modules/fsevents/package.json'
Target //:bundle failed to build
Use --verbose_failures to see the command lines of failed build steps.
INFO: Elapsed time: 0.606s, Critical Path: 0.02s
INFO: 9 processes: 9 internal.
FAILED: Build did NOT complete successfully
FAILED: Build did NOT complete successfully
```

This appears to be because `fsevents` is not installed due to it being
unsupported on Linux platforms. however, it is only an optional dependency for
Rollup per the NPM warning, so this *should* still work.

For whatever reason, using `npm ci` instead of `npm install` actually installs
`fsevents` and works.

```
$ /bin/rm -rf node_modules/ && bazel clean && npm ci && bazel test //...     
INFO: Invocation ID: 4cbb1ab7-faa2-4265-b399-e0ebad80555d
INFO: Starting clean (this may take a while). Consider using --async if the clean takes more than several minutes.

> @bazel/rollup@3.0.0 postinstall /home/dparker/Source/rollup_v3/node_modules/@bazel/rollup
> node npm_version_check.js

added 6 packages in 1.465s
INFO: Invocation ID: 6a9db41f-ff6e-4234-94dc-21247e7931d9
INFO: Analyzed target //:bundle (30 packages loaded, 129 targets configured).
INFO: Found 1 target and 0 test targets...
Target //:bundle up-to-date:
  dist/bin/bundle.js
INFO: Elapsed time: 0.611s, Critical Path: 0.01s
INFO: 10 processes: 1 remote cache hit, 9 internal.
INFO: Build completed successfully, 10 total actions
INFO: Build completed successfully, 10 total actions
```
