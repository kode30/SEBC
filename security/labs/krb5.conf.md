```
[logging]
 default = FILE:/var/log/krb5libs.log
 kdc = FILE:/var/log/krb5kdc.log
 admin_server = FILE:/var/log/kadmind.log

[libdefaults]
 default_realm = C.SAFARI-LAB.INTERNAL
 dns_lookup_realm = false
 dns_lookup_kdc = false
 ticket_lifetime = 24h
 renew_lifetime = 7d
 forwardable = true
 udp_preference_limit = 1
 default_tgs_enctypes = arcfour-hmac
 default_tkt_enctypes = arcfour-hmac 

[realms] 
  C.SAFARI-LAB.INTERNAL = {
  kdc = cdh-srv1.c.safari-lab.internal
  admin_server = cdh-srv1.c.safari-lab.internal
 }

[domain_realm]
   .c.safari-lab.internal = C.SAFARI-LAB.INTERNAL
   c.safari-lab.internal = C.SAFARI-LAB.INTERNAL
``` 
