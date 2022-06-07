# End of Life Spec

A specification for a software end of life format.

## Rationale

There is a gap in software lifecycle management: each project has its
own lifecycle and publishes the end of life dates and details in a
different format and place. That's why it is very difficult to make
decisions about which product version is the right one to pick in the
long term.

## Specification

Each end of life specification is a JSON object with the following
fields:

* `project`
  (String, mandatory):
  The name of the project.
* `homepage`
  (String, optional):
  The official homepage of the project.
* `end-of-life`
  (Array, mandatory):
  List of project versions with the  following end of life fields:
  * `version`
    (String, mandatory):
    A product version.
  * `notes`
    (String, optional):
    Release notes URL for that version.
  * `released`
    (String, optional, example: `YYYY-MM-DD`):
    The date the version was released.
  * `long-term-support`
    (Boolean, optional, default: `false`):
    Whether that version is long-term supported.
  * `bug-fixes-until`
    (String, mandatory, format: `YYYY-MM-DD`):
    The date the bug fixes for that version are expected to be fixed.
  * `security-fixes-until`
    (String, mandatory, format: `YYYY-MM-DD`):
    The date the security fixes for that version are expected to be
    fixed.
  * `running-on`
    (Array, optional):
    List of other project versions that the version is running on:
    * `project`
      (String, mandatory):
      The name of another project, hopefully having an end of life
      specification too.
    * `versions`
      (Array, mandatory):
      List of _that other project versions_ (String) that
      **root project version** is running on.

## Next steps

1. Spread the specification to everybody interested.
2. Curate an open list of specs for well established projects.
3. Get projects to publish their own end of life specs.

## Future

Once this specification is stable, a new
[well-known URI](https://www.iana.org/assignments/well-known-uris/well-known-uris.xhtml)
should be
[registered](https://github.com/protocol-registries/well-known-uris).
For instance:

```
https://example.org/.well-known/end-of-life
```

## Copyright and License

Copyright 2022 Alex Muntada

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
