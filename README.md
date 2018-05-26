# Gnarly Demo

> This is a super simple demo of how gnarly and paperboy work together to produce an event feed.

It uses the `:demo` tags of `shrugs/gnarly-test` and `shrugs/paperboy`, which may eventually be out of date.

## Setup

This demo relies on `docker-compose`. If you don't have it already, [install docker](https://docs.docker.com/install/) and then install [docker-compose](https://docs.docker.com/compose/install/). Install instructions vary between machines, so [check the website](https://docs.docker.com/install/) for up-to-date docs.

_Note: unfortunately, gnarly and paperboy don't attempt reconnects on failure just yet, so the services need to be started in the correct order._

1. `docker-compose up -d postgres` and wait for it to be happy (~5 seconds), then
2. `docker-compose up -d gnarly`
3. in a separate window `docker-compose logs -f gnarly`
4. `docker-compose up -d paperboy`
