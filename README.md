# To build docker file
docker build -t go-pipeline-demo:dev .

# To test Image
docker run --rm go-pipeline-demo:dev

# We can assign a version to the image
docker build -t go-pipeline-demo:1.0.0 . --build-arg VERSION=1.0.0

The reason this works, is because we use -ldflags to modify the version variable at compile time. The --build-arg assigns the version to VERSION and is used in the following line:

RUN go build -o main -ldflags=-X=main.version=${VERSION} main.go


