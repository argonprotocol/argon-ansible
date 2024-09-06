Rolls up several local prometheus providers into a single authorized ngnix server with multipled endpoints (basic auth).

Activates the following prometheus exporters:
- node_exporter
- nginx_exporter
- ws_exporter

Endpoints to scrape for prometheus:
- /substrate-metrics # substrate node metrics 
- /nginx-metrics # nginx metrics
- /ws-metrics # ws metrics
- /node-metrics # machine metrics
