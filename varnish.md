Varnish commands
==============

### Check config syntax
`varnishd -C -f /etc/varnish/default.vcl`

### Varnish histogram to show hit/miss
`varnishhist`

### Varnish log
`varnishlog`

### Varnish top
`varnishtop`

### Filter only some URL
`varnishlog  -q 'ReqURL ~ "^/someurl"'`

### Show what caused recent 503 errors
`varnishlog -c -m TxStatus:503`

### Show backend (probe) status
via `varnishstat`
