---
title: "Installation"
description: "Installation Steps"
weight: 3
---

{{< tip "warning" >}}
Current releases/images of Bench-routes is not suitable for production loads. If you face any issues, please
consider opening issues [here](https://github.com/bench-routes/bench-routes/issues).
{{< /tip >}}

Bench-routes can be installed in 2 ways:

1. Bare metal
2. Docker
3. Installing from source

## Bare metal

This is for installing and running Bench-routes locally using a pre-release binary. Here is an example to download the
amd64 version of `v1.0.0-alpha.2` release.

```shell
# Download the pre-release version
wget -O bench-routes.tar.gz https://github.com/bench-routes/bench-routes/releases/download/v1.0.0-alpha.2/src-linux-amd64.tar.gz

# Extract the tar file
tar -zxvf bench-routes.tar.gz 

# Change directory
cd build/src-linux-amd64

# Run
./src-linus-amd64.sh
```

This should be enough to turn on Bench-routes. You should get something like this in the logs.

```shell
[hsingh@localhost src-linux-amd64]$ ./src-linux-amd64.sh 
LOG:    2021/03/10 21:59:14.263315 main.go:55 initializing...
LOG:    2021/03/10 21:59:14.266505 main.go:295 forming req_res chain ... 
https://www.google.co.insearch
LOG:    2021/03/10 21:59:14.266584 main.go:295 forming flood_ping chain ... 
LOG:    2021/03/10 21:59:14.266688 db.go:132 creating chain at storage/req-res-delay-monitoring/chunk_req_res_https___www.google.co.in_search.json
LOG:    2021/03/10 21:59:14.266736 db.go:132 creating chain at storage/flood-ping/chunk_flood_ping_google.co.in.json
LOG:    2021/03/10 21:59:14.266749 main.go:295 forming jitter chain ... 
LOG:    2021/03/10 21:59:14.266808 main.go:295 forming ping chain ... 
LOG:    2021/03/10 21:59:14.266926 db.go:132 creating chain at storage/ping/chunk_ping_google.co.in.json
LOG:    2021/03/10 21:59:14.266873 db.go:132 creating chain at storage/jitter/chunk_jitter_google.co.in.json
https://www.facebook.comsearch
LOG:    2021/03/10 21:59:14.267624 db.go:132 creating chain at storage/req-res-delay-monitoring/chunk_req_res_https___www.facebook.com_search.json
LOG:    2021/03/10 21:59:14.267817 db.go:132 creating chain at storage/jitter/chunk_jitter_facebook.com.json
LOG:    2021/03/10 21:59:14.267914 db.go:132 creating chain at storage/flood-ping/chunk_flood_ping_facebook.com.json
https://in.search.yahoo.comsearch
LOG:    2021/03/10 21:59:14.268023 db.go:132 creating chain at storage/ping/chunk_ping_facebook.com.json
LOG:    2021/03/10 21:59:14.268106 db.go:132 creating chain at storage/req-res-delay-monitoring/chunk_req_res_https___in.search.yahoo.com_search.json
LOG:    2021/03/10 21:59:14.268163 db.go:132 creating chain at storage/jitter/chunk_jitter_in.search.yahoo.com.json
LOG:    2021/03/10 21:59:14.268211 db.go:132 creating chain at storage/flood-ping/chunk_flood_ping_in.search.yahoo.com.json
LOG:    2021/03/10 21:59:14.268397 main.go:326 finished req_res chain
LOG:    2021/03/10 21:59:14.268360 db.go:132 creating chain at storage/ping/chunk_ping_in.search.yahoo.com.json
LOG:    2021/03/10 21:59:14.268639 main.go:326 finished jitter chain
LOG:    2021/03/10 21:59:14.268730 main.go:326 finished flood_ping chain
LOG:    2021/03/10 21:59:14.268806 main.go:326 finished ping chain
LOG:    2021/03/10 21:59:14.268891 main.go:89 initial chain formation time: 2.503946ms
LOG:    2021/03/10 21:59:14.268939 main.go:93 Bench-routes is up and running
```

## Docker

Right now, we do not provide docker builds at docker hub. This will be done once the projecct moves to `beta` version.
But that does not mean you cannot use docker to make your life easier. We have a
[dockerfile](https://github.com/bench-routes/bench-routes/blob/master/Dockerfile) for this purpose.

You can clone the repository and then in the root folder, execute

```shell
# Build the image in your local docker registry
docker build -t bench-routes:local-latest .

# Run
docker run -p 9990:9990 -it bench-routes:local-latest
```

This should start running Bench-routes in the current terminal.

## Install from source

Since the project is in active development in early stages, the recent master commits will always be more stable than
the alpha releases. This makes a lot of sense to install and use the most recent code from development.

You can install and run from source in 3 ways:

1. Using `makefile`
2. Building the project

{{< tip "info" >}}
Note: Please ensure that the installed `go` version satisfies `1.15.x` and above.
{{< /tip >}}

#### Using `makefile`

[Makefile](https://www.gnu.org/software/make/manual/make.html) is used to ease the software development process. In order
to start running Bench-routes

```shell
make run
```

This simply runs the following command

```shell
go run src/*.go 9990
```

This means that you can also use that command to run directly.

Note: If you want to run Bench-routes at a port other than `:9990`, just change the last argument to the port you
want to keep.

#### Building the project

You can make a binary file and simply run it.

```shell
# Build
go build -o bench-routes ./src/*.go

# Run
./bench-routes
```

{{< tip "info" >}}
This documentation is open-source. Please help improve it by filing issues or pull requests [here](https://github.com/bench-routes/website).
{{< /tip >}}
