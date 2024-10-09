# Project Template

## Install Kratos

```bash
go install github.com/go-kratos/kratos/cmd/kratos/v2@latest
```

## Create Service

```bash
# Create a template project
kratos new server
cd server

# Add a proto template
kratos proto add api/server/server.proto

# Generate the proto code
kratos proto client api/server/server.proto

# Generate the source code of service by proto file
kratos proto server api/server/server.proto -t internal/service

go generate ./...
go build -o ./bin/ ./...
./bin/server -conf ./configs
```

## Makefile Generate

```bash
# Download and update dependencies
make init

# Generate API proto files
make api

# Generate all files
make all
```

## Automated Initial

```bash
# install wire
go get github.com/google/wire/cmd/wire

# generate wire
cd cmd/server
wire
```

## Docker Image

```bash
# build
docker build -t <your-docker-image-name> .

# run
docker run --rm -p 8000:8000 -p 9000:9000 -v </path/to/your/configs>:/data/conf <your-docker-image-name>
```
