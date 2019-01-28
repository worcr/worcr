## About

Worcr is a [Redis](https://redis.io)-based MIT-licensed background job processing framework. It is extremely fast (100k no-op jobs per second on a single process) and reliable. Worcr is built on [Crystal](https://crystal-lang.org), which syntax is pretty much similar to Ruby's:

```crystal
require "worcr-job"

struct Jobs::Greeter < Worcr::Job
  def initialize(@email : String)
  end
  
  def perform
    send_greeting_email(@email)
  end
end
```

## Features

Worcr is an [open-core](https://en.wikipedia.org/wiki/Open-core_model) software. The open-source MIT version has the following features:

* Enqueueing jobs
* Scheduling jobs
* Forced job timeouts
* Tracking completed and failed jobs
* Gentle worker termination
* Redis-based Web UI

### Pro

Pro version is designed for use within start-ups and small businesses:

* Forced retriable jobs with checkpoints
* Expiring jobs
* Job concurrency limits
* Dedicated support on the [Twist](https://twist.com) team

### Enterprise

Enterprise version is intended to use within companies with high load and many employees. Along with ones mentioned in Pro, it brings the following features:

* Native Redis cluster support
* PostgreSQL back-end for scheduled jobs, job statistics, user authentication and notifications
* Web UI with grained access to the PostgreSQL back-end
* Jobs rate limiting (including unique jobs)
* CRON scheduling

## Getting started

To get started with Worcr, please follow [this guide]().

## Support and troubleshooting

The MIT Worcr version is fully open-source, which means that you can open issues and PRs as you would in any other project. For communication purposes you may attend to the [official Gitter chat]() or follow the [official Twitter account]().

For extended support you can purchase Pro or Enterprise license, which will give you an access to the private [Twist](https://twist.com) team, where you're much more likely to get a professional answer in a timely manner.
