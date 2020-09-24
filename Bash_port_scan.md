# Escaneo de puertos usando BASH

for ip in $(seq 1 254); do ping -c 1 0.0.0.$ip > /dev/null && echo “Online: 0.0.0.$ip”; done

for port in "puertos"; do (echo > /dev/tcp/0.0.0.0/$port && echo “open – $port”) 2> /dev/null; done

for i in {1..65535}; do (echo < /dev/tcp/ip/$i) &>/dev/null && printf "\n[+] Puerto abierto\n: \t%d\n" "$i" || printf "."; done

for ip in $(seq 1..254); do ping -c 1 0.0.0.$ip > /dev/null && echo “Online: 0.0.0.$ip”; done

(echo > /dev/tcp/<host>/<port>) > /dev/null 2>&1 && echo "abierto" || echo "cerrado"
