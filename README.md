# pg-stats

Easily export data from your postgres database to prometheus by deploying a single chart in kubernetes.

## How to

pg-stats uses the docker image from https://github.com/wrouesnel/postgres_exporter that can run sql queries and expose the results in prometheus format.

The chart we propose contains additional queries that will help you to visualize the behaviour of your databases, schemas, tables and indexes.

To install the chart, you simply need to override the database url: 

    $ git clone https://github.com/Ouest-France/pg-stats
    $ cd pg-stats
    $ helm install --set databaseUrl=postgresql://user:password@database.domain.com:5432/dbname ./pg-stats

And voila!

Note: depending on the configuration of your prometheus scraper, you might need to adjust the labels / port of the service. In the current configuration, we expect prometheus to scrape the services exposing a port named `http-metrics`.

## Dashboards

You can find in the `dashboards` directory the grafana dashboards that will help you to visually analyse your database.

You simply need to import them in grafana http://docs.grafana.org/reference/export_import/#importing-a-dashboard

![](dashboard-tables.png)

# Authors

 - [Alexandre BARON](https://github.com/snapitch)
 - [Mathieu POUSSE](https://github.com/mathieu-pousse)