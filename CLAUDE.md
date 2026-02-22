# StageChat Runbook

## Starten
Voer uit vanuit de project-root:

```sh
nohup .venv/bin/python app.py > /tmp/stagechat_server.log 2>&1 & echo $!
```

Dit geeft de PID terug. StageChat hoort daarna te luisteren op poorten `80`, `443` en `8443`.

Controle:

```sh
lsof -nP -iTCP -sTCP:LISTEN | rg 'Python|:80|:443|:8443'
```

Live logs:

```sh
tail -f /tmp/stagechat_server.log
```

## Stoppen
Stop de server met de PID die je bij starten kreeg:

```sh
kill <PID>
```

Als je de PID kwijt bent, zoek die dan zo op:

```sh
lsof -nP -iTCP:8443 -sTCP:LISTEN
```
