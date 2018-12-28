CXXFLAGS ?= -I../../../include -I/home/henry/evolvability/protobuf/install/include -L/usr/local/lib/
LDFLAGS ?=

.PHONY: all
all: server client

greeter_generated.h: greeter.fbs
	flatc --grpc --cpp $<

server: server.cpp greeter.grpc.fb.cc greeter_generated.h greeter.grpc.fb.h
	g++ -std=c++11 -O2 $(CXXFLAGS) $(LDFLAGS) -lgpr -lgrpc -lgrpc++ -lgrpc_cronet -lgrpc++_cronet -lgrpc++_error_details -lgrpc++_reflection -lgrpc_unsecure -lgrpc++_unsecure  server.cpp greeter.grpc.fb.cc -o $@

client: client.cpp greeter.grpc.fb.cc greeter_generated.h greeter.grpc.fb.h
	g++ -std=c++11 -O2 $(CXXFLAGS) $(LDFLAGS) -lgpr -lgrpc -lgrpc++ client.cpp greeter.grpc.fb.cc -o $@
