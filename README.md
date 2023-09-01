<picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://traffic-control-cdn.readthedocs.io/en/latest/_static/ATC-SVG-FULL-WHITE.svg">
    <source media="(prefers-color-scheme: light)" srcset="https://trafficcontrol.apache.org/resources/Traffic-Control-Logo-FINAL-Black-Text.png">
    <img alt="Traffic Control Logo" src="https://trafficcontrol.apache.org/resources/Traffic-Control-Logo-FINAL-Black-Text.png">
</picture>

**Organization: [Apache](https://www.apache.org/)**

**Apache Project: [Traffic Control](https://trafficcontrol.apache.org/)**

**Project: [Varnish Cache support in Apache Traffic Control](https://summerofcode.withgoogle.com/programs/2023/projects/Y9YXNhle)**

**Mentors: [Eric Friedrich](https://github.com/limited), Traffic Control Dev Team (dev@trafficcontrol.apache.org)**

## Motivation

Traffic Control is a large scale Content Delivery Network (CDN) that uses Apache Traffic Server as the underlying cache server to manage caching content and delivering it. The different configuration files for ATS is generated and managed by `t3c` (traffic control cache config) while cache server load and statistics are being exposed and managed by `astats` plugin and polled by Traffic Monitor.
The goal of this project is to extend Traffic Control capabilities and add Varnish as a different option for the underlying cache server.

## Project Goals

From a high level perspective the project is mainly separated into two parts:

- Extend `t3c` to generate configuration for Varnish using Varnish Configuration Language (VCL).
- Monitor Varnish state by extending Traffic Monitor to poll Varnish.

## Achievements

- Added a Blueprint describing the changes in each of Traffic Control components (https://github.com/apache/trafficcontrol/pull/7620).
- Described in details how different ATS configuration can be done using VCL ([Varnish Support Wiki](https://github.com/apache/trafficcontrol/wiki/Varnish-Support)).
- Implemented `varnishcfg` package for Varnish configuration generation based on cache server parameters and data retrieved from Traffic Ops APIs:
  - Configure Varnish to operate in a multi-layer cache group (https://github.com/apache/trafficcontrol/pull/7669).
  - Configure access control over Varnish cache servers to control which IPs are allowed to do certain request methods like PURGE, PUSH and DELETE (https://github.com/apache/trafficcontrol/pull/7700).
  - Add HTTPs support to Varnish cache servers by using Hitch (https://github.com/apache/trafficcontrol/pull/7725).
- Added `vstats` to report Varnish cache load and added the new format to Traffic Monitor (https://github.com/apache/trafficcontrol/pull/7746).

## Future Work

- Continue working on unfinished configurations (Storage and Plugins).
- Aggregate Varnish statistics and report them to Traffic Stats.
- Add Varnish to Traffic Control Ansible deployment.
- Extend `t3c` docker tests with Varnish tests.
- Could work on making Go bindings for Varnish C APIs to be able to write VMODs in Go (still not sure if possible).

## Acknowledgments

I want to give special thanks to my mentors, Eric Friedrich and the Dev team, for their great support and guidance throughout the project. I learned a lot from their invaluable feedback and helpful comments. I would not have reached this state in the project without their help. Thank You!

Also, I wanted to thank Google for offering this opportunity to work with such great communities!

## Contact Me

- [Linkedin](https://www.linkedin.com/in/abdulrahmanelawady/)
- abdoelawady125@gmail.com
