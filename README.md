## About

Worcr is a GPL-licensed background job processor. It is extremely fast (up to **100k** no-op jobs per second on a single process) and doesn't have any back-end dependencies (it uses embedded SQLite database). Worcr is built on [Crystal](https://crystal-lang.org), which syntax is pretty much similar to Ruby's:

```crystal
require "worcr/worker"
require "worcr/job"

struct Jobs::Email::Greet
  include Worcr::Job
  
  def initialize(@email : String)
  end
  
  def perform(client)
    client.send(@email, "Welcome!")
  end
end

class Workers::Emailer < Worcr::Worker(Jobs::Email::Greet)
  def initialize
    @client = EmailClient.new(ENV["API_TOKEN"])
  end
  
  def perform(job)
    job.perform(client)
  end
end

worker = Workers::Emailer.new
worker.work
```
