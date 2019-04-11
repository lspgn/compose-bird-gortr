# Compose Bird 2.x and GoRTR

This repository contains a few configurations files to setup
two Bird talking to each others and one talking to a GoRTR.

Just run:
`docker-compose up`
The first start may take some time.

## Bird

There is no easily available binary for Bird 2.x.
I wrote a multi-stage Dockerfile that will build it
with SSH+RPKI support.

## Configuration

```
protocol rpki gortr {
     roa4 { table t_roa4; };
     roa6 { table t_roa6; };

     remote "10.1.0.4" port 8282;

     retry keep 90;
     refresh keep 900;
     expire keep 172800;
}
```
