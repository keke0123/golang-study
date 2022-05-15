BINARY_NAME=enterprise-conference-member

air_build: air_clean wire
air_build:
	GOARCH=amd64 GOOS=darwin go build -o ./tmp/main ./cmd/main.go
air_clean:
	go clean
	rm -r ./tmp

# build: clean pre_build
build: wire clean
build:
	GOARCH=amd64 GOOS=linux go build -o ./build/${BINARY_NAME}-linux ./cmd/main.go
	zip ./build/function.zip ./build/${BINARY_NAME}-linux;
# GOARCH=amd64 GOOS=darwin go build -o ./build/${BINARY_NAME}-darwin main.go
# GOARCH=amd64 GOOS=window go build -o ./build/${BINARY_NAME}-windows main.go

run: export PORT=8080
run:
	$(shell go env GOPATH)/bin/air

build_and_run: build run

clean:
	go clean
	rm -r ./build
# rm ${BINARY_NAME}-darwin
# rm ${BINARY_NAME}-linux
# rm ${BINARY_NAME}-windows

wire:
	echo "wire build..."
	$(shell go env GOPATH)/bin/wire ./...

