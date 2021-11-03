# Iot- Temperature

Proyecto experimental de IoT para monitorizar la temperatura de las distintas vacunas.
## Descripción

En cada aula del centro vacunatorio vamos a tener conectado a la heladera un sensor de temperatura montado sobre un arduino que va a ir tomando medidas de forma constante y las van a ir publicando en un *topic* de un [*broker* MQTT](http://mqtt.org). Podríamos seguir la siguiente estructura de nombres para los *topics* de la solución:

```
unla | ioma /heladera-<id>/vacuna-<id>/temperature
```

Por ejemplotendríamos los siguientes *topics*:

```
unla/sputnik/heladera-1/temperature
unla/sputnik/heladera-2/temperature
ioma/sputnik/heladera-3/temperature
```

También existirá un agente de [Telegraf](https://www.influxdata.com/time-series-platform/telegraf/) que estará suscrito a los  *topics* del [*broker* MQTT](http://mqtt.org) donde se publican los valores recogidos por los sensores.  El agente de [Telegraf](https://www.influxdata.com/time-series-platform/telegraf/) insertará los valores que recoge del [*broker* MQTT](http://mqtt.org) en una base de datos [InfluxDB](https://www.influxdata.com/), que es un sistema gestor de bases de datos diseñado para almacenar series temporales de datos.Finalmente tendremos un servicio web [Grafana](https://grafana.com) que nos permitirá visualizar los datos en un panel de control.

## Diagrama

![](images/diagram.png)

## Panel de control en Grafana

// Añadir imagen del dashboard

## Referencias
- https://github.com/josejuansanchez/co2-celia
- http://josejuansanchez.org/iot-dashboard/
- https://github.com/maarten-pennings/CCS811
