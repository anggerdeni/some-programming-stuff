# How to Run

```
docker network create -d ipvlan \
    --subnet=192.168.0.0/24 \
    --gateway=192.168.0.1 \
    -o parent=enp0s3 ipvlan_l2
```

enp0s3 is the host interface


Make it so that the speed is adjustable via argument ?

```
docker build -t speedtest-limited .
```


```
docker run --cap-add=NET_ADMIN -it --name container1 --rm --network ipvlan_l2 --ip=192.168.0.111 tc_htb_demo
```
