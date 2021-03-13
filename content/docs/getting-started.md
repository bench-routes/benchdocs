---
title: "Getting started"
description: "Getting started with Bench-Routes"
weight: 2
---

This is a guide to get started with the project. This is written more like a `hello-world` like manner, in order to
keep it simple.

Running Bench-routes is pretty straight forward. You require 2 files mostly:
1. Binary file
2. Configuration file (as `local-config.yml`)

The binary file can be downloaded and installed by following the instructions from [here](install.md). Once you have downloaded
you need to ensure that you have a `local-config.yml` file.

By default, Bench-routes is configured to consider `local-config.yml` as the default config though this can change
in stable releases.

If you have followed the instructions by now from installation to making sure that config file is present, you can safely
run bench-routes. Based on your method of installation, you can run it:
1. `./bench-routes`
2. `go run ./src/*.go`
3. `make run`

You should have Bench-routes running at port `:9990` as default.

{{< tip "info" >}}
This documentation is open-source. Please help improve it by filing issues or pull requests [here](https://github.com/bench-routes/website).
{{< /tip >}}
