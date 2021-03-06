uwsgi-riemann
=============

(WORK IN PROGRESS, only the stats pusher is implemented)

uWSGI plugin for riemann (http://riemann.io) integration

It implements:

* stats pusher
* alarm
* hook

Building it
-----------

The plugin is 2.0-friendly so you can build it directly from your uWSGI binary:

```sh
uwsgi --build-plugin uwsgi-riemann
```

since uWSGI 2.0.3 you can git-clone and build in one shot:

```
uwsgi --build-plugin https://github.com/unbit/uwsgi-riemann
```

You can even build a uWSGI binary with the riemann plugin embedded:

```
curl http://uwsgi.it/install | UWSGI_EMBED_PLUGINS="riemann=https://github.com/unbit/uwsgi-riemann" bash -s psgi /tmp/uwsgi
```

or (from the sources directory):

```
UWSGI_EMBED_PLUGINS="riemann=https://github.com/unbit/uwsgi-riemann" make
```

or (via pip)

```
UWSGI_EMBED_PLUGINS="riemann=https://github.com/unbit/uwsgi-riemann" pip install uwsgi
```

or (via gem)

```
UWSGI_EMBED_PLUGINS="riemann=https://github.com/unbit/uwsgi-riemann" gem install uwsgi
```

and so on...

Using it
========

Once loaded it register a stats-pusher, an alarm action and a hook.

For pushing stats to the riemann server 192.168.173.22:5555

just use

```ini
[uwsgi]
plugin = riemann
enable-metrics = true
stats-push = riemann:192.168.173.22:5555
...
```
