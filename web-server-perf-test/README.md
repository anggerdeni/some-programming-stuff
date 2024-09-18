# Web Server Perf Test Generator

The idea is create a program to generate several docker containers (or maybe just two with one spawning multiple process go routines idk) with limited bandwidth (ingress & egress).
- load-tester which will generate traffic
- web-server which will handle the traffic

For simplicity, we will make it requirement that the web-server accepts the GET request to root. The load tester is required to send different size of request: 1, 10, 100, 1_000, 10_000, 100_000, 1_000_000.

Preferably generate a dashboard (maybe grafana dashboard?).

## Input
- source & dockerfile to build the web server

## Updates
- 2024-09-18 20:58 - Initialize the project
- 2024-09-18 21:07 - Created dockerfile builder for [vegeta](https://github.com/tsenart/vegeta)
- 2024-09-18 21:12 - Setup docker compose for testing container bandwidth using unofficial [speedtest](https://github.com/robinmanuelthiel/speedtest) docker image
- 2024-09-18 21:28 - Read about bandwidth limitting for containers, and it turns out to be not as simple as I had imagined. Good article [here](https://hechao.li/2023/08/28/container-bandwidth-limit/)
- 2024-09-18 21:59 - Setup VM for lab purpose since I don't wanna mess around with my main host tc configurations

## Things I learned
- `tc` is a thing
- `iperf3` is a thing
- network manipulation on container is not straightforward
