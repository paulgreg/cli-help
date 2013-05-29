Varnish commands
==============

### Show hit/miss histogram
`varnishhist`

### Status code stats
`varnishtop -i TxStatus`

### Show referrer’s request
`varnishtop -i RxHeader -I \^Referer`

### Filter only some URL
`varnishlog -c -m Hash:/some/url`

### Show requests not cached
`varnishtop -b -i TxURL`

### Show what caused recent 503 errors
`varnishlog -c -m TxStatus:503`

