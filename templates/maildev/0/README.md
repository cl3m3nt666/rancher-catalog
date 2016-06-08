# Maildev

MailDev is a simple way to test your projects' emails during development with an easy to use web interface that runs on your machine.
https://github.com/djfarrelly/MailDev http://danfarrelly.nyc/MailDev/

## Usage

Enabling the auto relay mode will automatically send each email to it's recipient
without the need to click the "Relay" button mentioned above.
The outgoing email options are required to enable this feature.

Additionally, you can pass a valid json file with additional configuration for
what email addresses you would like to allow or deny. The last matching
rule in the array will be the rule MailDev will follow.

    $ maildev --outgoing-host smtp.gmail.com \
              --outgoing-secure \
              --outgoing-user 'you@gmail.com' \
              --outgoing-pass '<pass>' \
              --auto-relay \
              --auto-relay-rules /config/file.json


file.json

```
    [
        { "allow": "*" },
        { "deny":  "*@test.com" },
        { "allow": "ok@test.com" },
        { "deny":  "*@utah.com" },
        { "allow": "johnny@utah.com" }
    ]
```
## Globale help

    maildev [options]

      -h, --help                    output usage information
      -V, --version                 output the version number
      -s, --smtp <port>             SMTP port to catch emails [1025]
      -w, --web <port>              Port to run the Web GUI [1080]
      --ip <ip address>             IP Address to bind services to [0.0.0.0]
      --outgoing-host <host>        SMTP host for outgoing emails
      --outgoing-port <port>        SMTP port for outgoing emails
      --outgoing-user <user>        SMTP user for outgoing emails
      --outgoing-pass <pass>        SMTP password for outgoing emails
      --outgoing-secure             Use SMTP SSL for outgoing emails
      --auto-relay                  Use auto relay mode
      --auto-relay-rules <file>     Filter rules for auto relay mode
      --incoming-user <user>        SMTP user for incoming emails
      --incoming-pass <pass>        SMTP password for incoming emails
      --web-ip <ip address>         IP Address to bind HTTP service to, defaults to --ip
      --web-user <user>             HTTP basic auth username
      --web-pass <pass>             HTTP basic auth password
      -o, --open                    Open the Web GUI after startup
      -v, --verbose
