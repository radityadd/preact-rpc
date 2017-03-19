# preact-rpc
React Pre-Rendering via RPC

A simple JSON based socket server that fulfills React component render requests.

The motivation for this project is to use React server-side rendering (aka pre-rendering) from a non-Node app, such as one
written in Ruby, or Go.

The preact-rpc server loads a Javascript bundle file containing the React components, and starts listening for render requests
on a socket (a TCP socket or a UNIX socket file). A client, such as a Go app, can connect to the server and send a render request
by providing a React component identifier and the props to use for rendering. The server returns with an HTML string, that can
then be embedded in a view served on the client side.

Starting the server is simple, and requires the path to the bundle file and the port to listen on:

  preact-rpc.js  --bundle=./lib/example/component.js --port=tmp/server.sock

An example Go client is provided in the example-clients directory. Run the app and visit http://localhost:8080

  go run example-clients/client.go

## More to come:
Add support for Redux stores