Go implementation of gRPC.

# PROTO
proto/service.proto -> definition of protobuf stubs for both client and server
proto/service.pb.go is a Go stub of properties and behaviours defined within "proto/service.proto". This file will be used to setup both client and server.

Generate "proto/service.pb.go"
> `$ protoc -I proto/ proto/service.proto --go_out=plugins=grpc:proto"` 

# SERVER
server/main.go -> Server source code
server/main.go starts a listener on 4040 and registers a gRPC server using "service.pb.go" file we generated earlier.
Also, Add and Multiply methods from "service.pb.go" need to be implemented to define the behaviour.

Start the gRPC server.
> `$ go run server/main.go`

# CLIENT
client/main.go -> Client source code
client/main.go dials a connection towards the server, it uses gin to setup an API through which we can pass parameters.

Start the gRPC client and the API.
> `$ go run client/main.go"`

# USAGE
## API: 
- localhost:8080/add/:a/:b
- localhost:8080/multiply/:a/:b

Make a GET Request to any of the routes within the API, where 'a' and 'b' are both integer values which you want added or multiplied.
