TriggerFail
===========

[![Build Status](https://travis-ci.org/phayes/triggerfail.svg?branch=master)](https://travis-ci.org/phayes/triggerfail)

Fail a command with an exit status of 82 if a trigger string appears in it's output. This is incredibly useful for use with testing framworks (such as Travis CI), which will let you fail a test if certain keywords like "Error" or "Warning" appears in it's output.

```sh
USAGE
  triggerfail "<space-seperated-strings>" [--abort] [-v] <command>

OPTIONS
  -abort=false: Abort a running command if a match is found. If abort is not passed the command is allowed to run to completion
  -v=false: Verbose. Print the reason why we failed the command.

EXAMPLE
  triggerfail --abort -v --stderr "Error Warning" mysqldump my_database > mysqlbackup.sql #Abort a running mysqldump if we encounter a warning or error.
```

####Downloads
 - Linux: https://phayes.github.io/bin/current/triggerfail/linux/triggerfail.gz
 - Mac:   https://phayes.github.io/bin/current/triggerfail/mac/triggerfail.gz

#### Building From Source
```bash
sudo apt-get install golang                    # Download go. Alternativly build from source: https://golang.org/doc/install/source
mkdir ~/.gopath && export GOPATH=~/.gopath     # Replace with desired GOPATH
export PATH=$PATH:$GOPATH/bin                  # For convenience, add go's bin dir to your PATH
go get github.com/phayes/triggerfail/cmd/triggerfail
