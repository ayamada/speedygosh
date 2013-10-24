speedygosh
==========

For Japanese
------------

日本語の分かる方は以下を参考にしてください。

- http://e.tir.jp/wiliki?speedygosh (for japanese)

ここには英語にて説明を書きます。内容自体は上のページと同じです。

Usage
-----

Change from `#!/path/to/gosh` to `#!/path/to/speedygosh` in [Gauche](http://practical-scheme.net/gauche/) script file.

( But, speedygosh has some constraints. See below. )

Summary
-------

- A speedygosh-ized script were booted, that boot backend process. A backend do to execute scripted code, but it is resident process.
- This script were booted more than once, that reuse existing backend process. it omit cost of boot-sequence(quicken to boot).
- A backend process is shutdowned automatically when idle while 90 sec (by default).
- It is convenience for CGI-script, and commonly-used CLI-command.
- This behavior is like to [SpeedyCGI](http://daemoninc.com/SpeedyCGI/), and [Heroku](https://www.heroku.com/about)-process.
  - speedygosh's behavior is like to SpeedyCGI (because I inspired by SpeedyCGI). To read [SpeedyCGI#FREQUENTLY ASKED QUESTIONS](http://daemoninc.com/SpeedyCGI/#FREQUENTLY_ASKED_QUESTIONS), that may help to understand speedygosh's behavior.

Requirements
------------

- Gauche-0.8.10 or later
- POSIX environment (I tested Gentoo Linux-3.0.6, FreeBSD 7.1-RELEASE-p16)

Install
-------

```sh
$ wget http://legacy.tir.jp/speedygosh-0.1.9.tgz
$ gauche-package install speedygosh-0.1.9.tgz
```

or

```sh
$ git clone git@github.com:ayamada/speedygosh.git # or your fork
$ cd speedygosh
$ ./DIST gen
$ ./configure
$ make all check install
```

for development

ChangeLog
---------

- https://github.com/ayamada/speedygosh/blob/master/ChangeLog (sorry, it written by japanese)

Args
----
You can add args like `#!/path/to/speedygosh --sessiondir=/home/user/tmp/sg`

NOTICE: MAYBE ONLY 1 ARG CAN USE DEPENDING BY OS TYPE

(maybe Linux can many args, but FreeBSD can only 1 arg)

- `-g ...` `--goshpath=...`
  - Change to original `gosh`'s path
  - Cannot include `~` alias (you must write `/home/username/`, instead of `~`)
  - Cannot include a space character

- `-d ...` `--sessiondir=...`
  - Change to dir of sock file and other
  - Default is "/tmp/speedygosh"
  - Cannot include `~` alias (you must write `/home/username/`, instead of `~`)
  - Cannot include a space character

- `-p ...` `--maxprocesses=...`
  - Limit of number of processes per one script
  - Default is 32
  - Cannot assign `0`

- `-r ...` `--maxruns=...`
  - A backend process was shutdowned by count of executing (for safety from resource leaks)
  - Default is 1024
  - Cannot assign `0`

- `-t ...` `--timeout=...`
  - A backend process was shutdowned automatically when idle while this secs
  - Default is 90
  - Cannot assign `0`

- `-e ...` `--errorlog=...`
  - Force to change stderr to this file with `>>` mode
  - Cannot include `~` alias (you must write `/home/username/`, instead of `~`)
  - Cannot include a space character

Constraints
-----------

TODO: later

(sorry, please use [translate.google.com](http://translate.google.com/#auto/en/http%3A%2F%2Flegacy.e.tir.jp%2Fwiliki%3Fspeedygosh))



