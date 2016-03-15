# Go Plugins [![GoDoc](https://godoc.org/github.com/micro/go-plugins?status.svg)](https://godoc.org/github.com/micro/go-plugins) [![Travis CI](https://travis-ci.org/micro/go-plugins.svg?branch=master)](https://travis-ci.org/micro/go-plugins) [![Go Report Card](https://goreportcard.com/badge/micro/go-plugins)](https://goreportcard.com/report/github.com/micro/go-plugins)

A repository for go-micro and go-platform plugins.

Contributions welcome! Join the community to discuss further.

- [Mailing List](https://groups.google.com/forum/#!forum/micro-services) 
- [Slack](https://micro-services.slack.com) : [auto-invite](http://micro-invites.herokuapp.com/)

## What's here?

Directory	|	Description
---		|	---
Broker		|	Asynchronous Pub/Sub; NATS, NSQ, RabbitMQ, Kafka	
Codec		|	RPC Encoding; BSON, Mercury
Registry	|	Service Discovery; Etcd, Gossip, NATS
Selector	|	Node Selection; Label, Mercury
Transport	|	Synchronous Request/Response; NATS, RabbitMQ
Wrappers	|	Client/Server middleware; Circuit Breakers

## Usage

Plugins can be added to go-micro in the following ways. By doing so they'll be available to set via command line args or environment variables.

```go
import (
	"github.com/micro/go-micro/cmd"
	_ "github.com/micro/go-plugins/broker/rabbitmq"
	_ "github.com/micro/go-plugins/registry/kubernetes"
	_ "github.com/micro/go-plugins/transport/nats"
)

func main() {
	cmd.Init()
}
```

OR use them directly

```go
import (
	"github.com/micro/go-plugins/registry/kubernetes"
)

func main() {
	r := kubernetes.NewRegistry([]string{}) // default to using env vars for master API
}
```