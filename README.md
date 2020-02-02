Go implementation of gRPC.

# PROTO
proto/ -> definition of protobuf stubs for both client and server

Use "$ protoc -I proto/ proto/service.proto --go_out=plugins=grpc:proto" to generate "proto/service.pb.go", 
a Go stub of properties and behaviours defined within "proto/service.proto"
Newly generated file will be used to setup both client and server.

# SERVER
server/main.go -> Server source code

Use "$ go run server/main.go" to start the gRPC server.
server/main.go starts a listener on 4040 and registers a gRPC server using "service.pb.go" file we generated earlier.
Also, Add and Multiply methods from "service.pb.go" need to be implemented to define the behaviour.

# CLIENT
client/main.go -> Client source code

Use "$ go run client/main.go" to start the gRPC client and the API.
client/main.go dials a connection towards the server, it uses gin to setup an API through which we can pass parameters.

API: 

- localhost:8080/add/:a/:b
- localhost:8080/multiply/:a/:b

# USAGE

Make a GET Request to any of the routes within the API, where 'a' and 'b' are both integer values which you want added or multiplied.
