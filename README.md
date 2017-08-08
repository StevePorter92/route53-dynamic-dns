# sjmayotte/route53-dynamic-dns
[![Docker Build Statu](https://img.shields.io/docker/build/sjmayotte/route53-dynamic-dns.svg)](https://hub.docker.com/r/sjmayotte/route53-dynamic-dns) [![FOSSA Status](https://app.fossa.io/api/projects/git%2Bhttps%3A%2F%2Fgithub.com%2Fsjmayotte%2Froute53-dynamic-dns.svg?type=shield)](https://app.fossa.io/projects/git%2Bhttps%3A%2F%2Fgithub.com%2Fsjmayotte%2Froute53-dynamic-dns?ref=badge_shield) [![](https://images.microbadger.com/badges/image/sjmayotte/route53-dynamic-dns.svg)](https://microbadger.com/images/sjmayotte/route53-dynamic-dns "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/sjmayotte/route53-dynamic-dns.svg)](https://microbadger.com/images/sjmayotte/route53-dynamic-dns "Get your own version badge on microbadger.com") [![Docker Pulls](https://img.shields.io/docker/pulls/sjmayotte/route53-dynamic-dns.svg)](https://hub.docker.com/r/sjmayotte/route53-dynamic-dns/)

Update [Amazon Route53](http://aws.amazon.com/route53/) hosted zone with current public IP address (from [OpenDNS](https://diagnostic.opendns.com/myip).  No cost alternative to DynamicDNS services such as Dyn, No-IP, etc.  Project is designed to be simple and efficient with the ability to run as a standalone node.js process or in a [Docker Container published on DockerHub](https://hub.docker.com/r/sjmayotte/route53-dynamic-dns/).

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Environment Variables](#environment-variables)
- [Usage](#usage)
  - [Standalone Node.js Process](#standalone-nodejs-process)
  - [Docker](#docker)
- [License](#license)
  - [MIT](#mit)
  - [Attribution](#attribution)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Environment Variables
Environment variables are required to run the process as standalone Node.js process or Docker Container.
* `AWS_ACCESS_KEY_ID` - `string` -  Secret Key ID from AWS account; see: [AWS Javascript SDK - Getting Started](http://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/getting-started-nodejs.html)
* `AWS_SECRET_ACCESS_KEY` - `string` - Secret Access Key from AWS account; see: [AWS Javascript SDK - Getting Started](http://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/getting-started-nodejs.html)
* `AWS_REGION` - `string` - AWS Region; ex: "us-east-1"; see: [AWS Javascript SDK - Setting Region](http://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-region.html)
* `ROUTE53_HOSTED_ZONE_ID` - `string` - AWS Route53 Hosted Zone ID; ex: "Z25S75OFY0ERQD"
* `ROUTE53_DOMAIN` - `string` - AWS Route53 FQDN; ex: "home.example.com"
* `ROUTE53_TYPE` - `string` - AWS Route 53 record type for FQDN; ex: "A"
* `ROUTE53_TTL` - `integer` - AWS Route 53 TTL in seconds for FQDN; ex: 60
* `SEND_EMAIL_SES` - `boolean` - Use AWS SES to send notification email. ex: true
* `SES_TO_ADDRESS` - `string` - If using AWS SES, this is to address for email; ex: admin@example.com   
* `SES_FROM_ADDRESS` - `string` - If using AWS SES, this is from address for email; ex: notification@example.com
* `UPDATE_FREQUENCY` - `integer` - Frequency in Milliseconds of check to update Public IP; ex: 60000, which is every minute

# Usage
Can be run as [standalone Node.js process](#standalone-node.js-process) or [Docker Container](#docker).  

## Standalone Node.js Process
**Clone Repository**
```bash
$ git clone https://github.com/sjmayotte/route53-dynamic-dns
$ cd route53-dynamic-dns
```

**Set Environment Variables**
You have the option to pass [Environment Variables](#environment-variables) at runtime or populate [Environment Variables](#environment-variables) in `.env`.  This repository contains `.env.example`, which can be renamed to `.env` and populated with values.  The process expects `.env` will be in root of directory structure.
```bash
$ cp .env.example .env
$ vi .env
```

**Installation**
```bash
$ npm install
```
```bash
$ npm start
```

## Docker
This image is built using official [`node:alpine`](https://hub.docker.com/_/node/) DockerHub image, which runs on the popular [Alpine Linux project](http://alpinelinux.org). Alpine Linux is much smaller than most distribution base images (~5MB), which leads to much slimmer images in general.

**Pull Image**
```bash
$ docker pull sjmayotte/route53-dynamic-dns
```

**Run Container**
```bash
$ docker run -d -t -i --rm \
    --name route53-dynamic-dns \
    -e AWS_ACCESS_KEY_ID= \
    -e AWS_SECRET_ACCESS_KEY= \
    -e AWS_REGION= \
    -e ROUTE53_HOSTED_ZONE_ID= \
    -e ROUTE53_DOMAIN= \
    -e ROUTE53_TYPE= \
    -e ROUTE53_TTL= \
    -e SEND_EMAIL_SES= \
    -e SES_TO_ADDRESS= \
    -e SES_FROM_ADDRESS= \
    -e UPDATE_FREQUENCY= \
    sjmayotte/route53-dynamic-dns
```

# License
## MIT
Route53 Dynamic DNS is licensed under the MIT License (https://opensource.org/licenses/MIT).  A copy of MIT License is included in this repository.

## Attribution
The following 3rd-party software components may be used by or distributed with route53-dynamic-dns: https://app.fossa.io/reports/f5377d5f-557e-4e21-8bfa-93a27ea6e540


[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bhttps%3A%2F%2Fgithub.com%2Fsjmayotte%2Froute53-dynamic-dns.svg?type=large)](https://app.fossa.io/projects/git%2Bhttps%3A%2F%2Fgithub.com%2Fsjmayotte%2Froute53-dynamic-dns?ref=badge_large)