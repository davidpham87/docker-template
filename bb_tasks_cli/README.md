# Tasks cli

This is an example how to add arguments to tasks.


# Example


``` shell

$ bb summary

> {:port 8083, :target "http://localhost:8052/api", :tag "native-test"}
  -p, --port PORT      Port number
  -t, --tag TAG        Tag
  -c, --config CONFIG  Config for arguments
  -h, --help           Show this help

$ bb summary -c config.edn

{:port 8080,
 :target "http://localhost:8052/api",
 :tag "native-test",
 :config "config.edn"}
  -p, --port PORT      Port number
  -t, --tag TAG        Tag
  -c, --config CONFIG  Config for arguments
  -h, --help           Show this help

```
