# component-signals - Settings component for shutdown signaling
[![GoDoc](https://godoc.org/github.com/asecurityteam/component-signals?status.svg)](https://godoc.org/github.com/asecurityteam/component-signals)

[![Bugs](https://sonarcloud.io/api/project_badges/measure?project=asecurityteam_component-signals&metric=bugs)](https://sonarcloud.io/dashboard?id=asecurityteam_component-signals)
[![Code Smells](https://sonarcloud.io/api/project_badges/measure?project=asecurityteam_component-signals&metric=code_smells)](https://sonarcloud.io/dashboard?id=asecurityteam_component-signals)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=asecurityteam_component-signals&metric=coverage)](https://sonarcloud.io/dashboard?id=asecurityteam_component-signals)
[![Duplicated Lines (%)](https://sonarcloud.io/api/project_badges/measure?project=asecurityteam_component-signals&metric=duplicated_lines_density)](https://sonarcloud.io/dashboard?id=asecurityteam_component-signals)
[![Lines of Code](https://sonarcloud.io/api/project_badges/measure?project=asecurityteam_component-signals&metric=ncloc)](https://sonarcloud.io/dashboard?id=asecurityteam_component-signals)
[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=asecurityteam_component-signals&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=asecurityteam_component-signals)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=asecurityteam_component-signals&metric=alert_status)](https://sonarcloud.io/dashboard?id=asecurityteam_component-signals)
[![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=asecurityteam_component-signals&metric=reliability_rating)](https://sonarcloud.io/dashboard?id=asecurityteam_component-signals)
[![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=asecurityteam_component-signals&metric=security_rating)](https://sonarcloud.io/dashboard?id=asecurityteam_component-signals)
[![Technical Debt](https://sonarcloud.io/api/project_badges/measure?project=asecurityteam_component-signals&metric=sqale_index)](https://sonarcloud.io/dashboard?id=asecurityteam_component-signals)
[![Vulnerabilities](https://sonarcloud.io/api/project_badges/measure?project=asecurityteam_component-signals&metric=vulnerabilities)](https://sonarcloud.io/dashboard?id=asecurityteam_component-signals)


<!-- TOC -->autoauto- [component-signals - Settings component for shutdown signaling](#component-signals---settings-component-for-shutdown-signaling)auto    - [Overview](#overview)auto    - [Quick Start](#quick-start)auto    - [Status](#status)auto    - [Contributing](#contributing)auto        - [Building And Testing](#building-and-testing)auto        - [License](#license)auto        - [Contributing Agreement](#contributing-agreement)autoauto<!-- /TOC -->

## Overview

This is a [`settings`](https://github.com/asecurityteam/settings) that enables
constructing a metrics gathering component that orchestrates fanning in various
shutdown signals for a system. It currently support OS signals but can be
extended to support other forms.

## Quick Start

```golang
package main

import (
    "context"
    "net/http"

    signals "github.com/asecurityteam/component-signals"
    "github.com/asecurityteam/settings/v2"
)

func main() {
    ctx := context.Background()
    envSource := settings.NewEnvSource(os.Environ())

    sig, _ := signals.New(ctx, envSource)

    <-sig
    fmt.Println("shut down")
}
```

## Status

This project is in incubation which means we are not yet operating this tool in
production and the interfaces are subject to change.

## Contributing

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

### License

This project is licensed under Apache 2.0. See LICENSE.txt for details.

### Contributing Agreement

Atlassian requires signing a contributor's agreement before we can accept a patch. If
you are an individual you can fill out the [individual
CLA](https://na2.docusign.net/Member/PowerFormSigning.aspx?PowerFormId=3f94fbdc-2fbe-46ac-b14c-5d152700ae5d).
If you are contributing on behalf of your company then please fill out the [corporate
CLA](https://na2.docusign.net/Member/PowerFormSigning.aspx?PowerFormId=e1c17c66-ca4d-4aab-a953-2c231af4a20b).
