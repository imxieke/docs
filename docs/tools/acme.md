# acme.sh
`~/.acme.sh/acme.sh --issue -d "api.xie.ke" -d '*.api.xie.ke' --dns --yes-I-know-dns-manual-mode-enough-go-ahead-please`

export CF_Key=""
export CF_Email="xxx@xxx.xxx"

~/.acme.sh/acme.sh --issue --dns dns_cf -d xieke.org -d *.xieke.org -d xie.ke -d *.xie.ke -d dev.dog -d *.dev.dog

## Cron Renew SSL
0 0 * * * "/root/.acme.sh"/acme.sh --cron --home "/root/.acme.sh" > /dev/null

~/.acme.sh/acme.sh --issue --dns dns_cf -d dev.dog -d *.dev.dog
~/.acme.sh/acme.sh --issue --dns dns_cf -d xie.ke -d *.xie.ke