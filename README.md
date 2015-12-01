# status.spodeli.org
status.spodeli.org - dashboard for hacklab status information (temperature, people, open/closed, budget, etc)

## Metrics database

Metrics are currently stored in [Influxdb](https://influxdb.com/docs/v0.9/introduction/overview.html) by the scripts in
[kika-info-bus](https://github.com/skopjehacklab/kika-info-bus/tree/master/influxdb-logger). Example queries:

```
curl -i -G 'https://db.softver.org.mk/influxdb/query?pretty=true' \
   --data-urlencode "db=status" \
   --data-urlencode "q=SELECT * FROM temperatures"
```

```
curl -i -G 'https://db.softver.org.mk/influxdb/query?pretty=true' \
   --data-urlencode "db=status" \
   --data-urlencode "q=SELECT * FROM landevices"
```

For the whole query language see the [influxdb documentation](https://influxdb.com/docs/v0.9/guides/querying_data.html).

Open/closed status is available at http://hacklab.ie.mk/status/ (regex for ^status: ...$), but this might also be
included in the influxdb TBBD.
