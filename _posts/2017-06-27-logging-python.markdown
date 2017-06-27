---
layout: post
title:  "setup logging in python"
date:   2017-06-27 14:46:58 +0200
categories: development
---
setting up logging in python projects could be pain in the ass sometimes.
you should remember logging format and configuration in every module even though
you want it consistent everywhere.

i found the most convenient way (for me) to have logging configuration in one
file (it could be JSON and YML but yaml is more readable to me)

you define one format and a couple of handlers and you are
good to go:

{% highlight yaml %}
---
version: 1
disable_existing_loggers: False
formatters:
    simple:
        format: "%(asctime)s - %(name)s - %(levelname)s - %(message)s"

handlers:
    console:
        class: logging.StreamHandler
        level: DEBUG
        formatter: simple
        stream: ext://sys.stdout

    info_file_handler:
        class: logging.handlers.RotatingFileHandler
        level: INFO
        formatter: simple
        filename: logs/info.log
        maxBytes: 10485760 # 10MB
        backupCount: 5
        encoding: utf8

    error_file_handler:
        class: logging.handlers.RotatingFileHandler
        level: ERROR
        formatter: simple
        filename: logs/errors.log
        maxBytes: 10485760 # 10MB
        backupCount: 10
        encoding: utf8

    debug_file_handler:
        class: logging.handlers.RotatingFileHandler
        level: DEBUG
        formatter: simple
        filename: logs/debug.log
        maxBytes: 10485760 # 10MB
        backupCount: 2
        encoding: utf8

loggers:
    your.module.one:
        level: INFO
        handlers: [console, info_file_handler, error_file_handler]
        propagate: no
    you].other.module:
        level: INFO
        handlers: [console, info_file_handler, error_file_handler]
        propagate: no

root:
    level: INFO
    handlers: [console, info_file_handler, error_file_handler]


{% endhighlight %}

in your python code you initialize it like this:

{% highlight python %}
def setup_logging(default_path=LOG_CONFIG, default_level=logging.DEBUG):

    path = os.path.join(os.getcwd(), default_path)

    if os.path.exists(path):
        with open(path, 'rt') as f:
            config = yaml.safe_load(f.read())
        logging.config.dictConfig(config)
    else:
        logging.basicConfig(level=default_level)

{% endhighlight %}
