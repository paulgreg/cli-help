Varnish commands
==============

### Check config syntax
`varnishd -C -f /etc/varnish/config.vcl`

### Varnish histogram to show hit/miss
`varnishhist`

### Varnish log
`varnishlog`

### Varnish top
`varnishtop`

### Status code stats
`varnishtop -i TxStatus`

### Show referrer’s request
`varnishtop -i RxHeader -I \^Referer`

### Show requests not cached
`varnishtop -b -i TxURL`

### Filter only some URL
`varnishlog -c -m Hash:/some/url`

### Show what caused recent 503 errors
`varnishlog -c -m TxStatus:503`

