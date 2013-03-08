Varnish commands
==============

### Show hit/miss histogram
`varnishhist`

### Status code stats
`varnishtop -i TxStatus`

### Show referrer’s request
`varnishtop -i RxHeader -I \^Referer`

### Show requests not cached
`varnishtop -b -i TxURL`

### Show what caused recent 503 errors
`varnishlog -d -c -o TxStatus 503`
