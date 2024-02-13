Varnish commands
==============

### Check config syntax
`varnishd -C -f /etc/varnish/default.vcl`

### Varnish histogram to show hit/miss
`varnishhist`

### Varnish top URL
`varnishtop -i ReqURL`

### Varnish log
`varnishlog`

### Filter only some URL
`varnishlog  -q 'ReqURL ~ "^/someurl"'`

### Show 50x errors
`varnishlog -q 'RespStatus >= 500 or BerespStatus >= 500'`

### Show backend (probe) status
via `varnishstat`
