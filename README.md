<a id="markdown-component-signals---settings-component-for-shutdown-signaling" name="component-signals---settings-component-for-shutdown-signaling"></a>
# component-signals - Settings component for shutdown signaling

<!-- TOC -->

- [component-signals - Settings component for shutdown signaling](#component-signals---settings-component-for-shutdown-signaling)
    - [Overview](#overview)
    - [Quick Start](#quick-start)
    - [Status](#status)
    - [Contributing](#contributing)
        - [Building And Testing](#building-and-testing)
        - [License](#license)
        - [Contributing Agreement](#contributing-agreement)

<!-- /TOC -->

<a id="markdown-overview" name="overview"></a>
## Overview

This is a [`settings`](https://github.com/asecurityteam/settings) that enables
constructing a metrics gathering component that orchestrates fanning in various
shutdown signals for a system. It currently support OS signals but can be
extended to support other forms.

<a id="markdown-quick-start" name="quick-start"></a>
## Quick Start

```golang
package main

import (
    "context"
    "net/http"

    signals "github.com/asecurityteam/component-signals"
    "github.com/asecurityteam/settings"
)

func main() {
    ctx := context.Background()
    envSource := settings.NewEnvSource(os.Environ())

    sig, _ := signals.New(ctx, envSource)

    <-sig
    fmt.Println("shut down")
}
```

<a id="markdown-status" name="status"></a>
## Status

This project is in incubation which means we are not yet operating this tool in
production and the interfaces are subject to change.

<a id="markdown-contributing" name="contributing"></a>
## Contributing

<a id="markdown-building-and-testing" name="building-and-testing"></a>
### Building And Testing

We publish a docker image called [SDCLI](https://github.com/asecurityteam/sdcli) that
bundles all of our build dependencies. It is used by the included Makefile to help
make building and testing a bit easier. The following actions are available through
the Makefile:

-   make dep

    Install the project dependencies into a vendor directory

-   make lint

    Run our static analysis suite

-   make test

    Run unit tests and generate a coverage artifact

-   make integration

    Run integration tests and generate a coverage artifact

-   make coverage

    Report the combined coverage for unit and integration tests

<a id="markdown-license" name="license"></a>
### License

This project is licensed under Apache 2.0. See LICENSE.txt for details.

<a id="markdown-contributing-agreement" name="contributing-agreement"></a>
### Contributing Agreement

Atlassian requires signing a contributor's agreement before we can accept a patch. If
you are an individual you can fill out the [individual
CLA](https://na2.docusign.net/Member/PowerFormSigning.aspx?PowerFormId=3f94fbdc-2fbe-46ac-b14c-5d152700ae5d).
If you are contributing on behalf of your company then please fill out the [corporate
CLA](https://na2.docusign.net/Member/PowerFormSigning.aspx?PowerFormId=e1c17c66-ca4d-4aab-a953-2c231af4a20b).
