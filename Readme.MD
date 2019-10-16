# Running

## nats
`docker run -d --name nats-main -p 4222:4222 -p 6222:6222 -p 8222:8222 nats`

## nat prometheus exporter

go get github.com/nats-io/prometheus-nats-exporter
prometheus-nats-exporter -varz -connz http://localhost:8222

## prometheus

`docker run --name prometheus --rm -d -p 9090:9090 -v ~/Dev/learnnats/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus` 

## grafana
`docker run -d --name=grafana -p 3000:3000 grafana/grafana`

User creds admin:admin

Add prometheus data source, specify url - host.docker.internal

import dashboard - https://github.com/nats-io/prometheus-nats-exporter/blob/master/walkthrough/grafana-nats-dash.json
# Patterns

*Setup*

Run `tmux` - split 3 views ( `Ctrl+b` `%` and `Ctrl+b` `"` ), `Ctrl+b` `arrows` to move around panes

## Pub + Sub

*Download*
`go get github.com/nats-io/go-nats-examples/tools/nats-pub`
`go get github.com/nats-io/go-nats-examples/tools/nats-sub`

*Run* 

`nats-pub -s localhost ">" "hello world"`
`nats-sub -s localhost ">"`   

## Request + Response

*Download*
go get github.com/nats-io/go-nats-examples/tools/nats-req
go get github.com/nats-io/go-nats-examples/tools/nats-rply

*Run*
`nats-rply -s localhost ">" "my response"`
`nats-req -s localhost ">" "my request`


