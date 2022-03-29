# ngrok API client library for Python

This library wraps the [ngrok HTTP API](https://ngrok.com/docs/api) to make it
easier to consume in Python.

## Beta Disclaimer

The Python ngrok API client library is in beta. While most of this
library should work, portions may be entirely broken or incomplete.

## Installation

This library is published on [PyPi](https://pypi.org/project/ngrok-api/)

    pip install ngrok-api

## Documentation

A quickstart guide and a full API reference are included in the [ngrok python API documentation](https://python-api.docs.ngrok.com)

## Quickstart

Please consult the [documentation](https://python-api.docs.ngrok.com) for additional examples.

    import ngrok

    # construct the api client
    client = ngrok.Client("<API KEY>")

    # list all online tunnels
    for t in client.tunnels.list():
        print(t)

    # create an ip policy that allows traffic from some subnets
    policy = client.ip_policies.create()
    for cidr in ["24.0.0.0/8", "12.0.0.0/8"]:
        client.ip_policy_rules.create(cidr=cidr, ip_policy_id=policy.id, action="allow")