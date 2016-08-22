# ANSIBLE ROLE TO CONFIGURE GENERIC LOGSTASH SHIPPER FOR MONITORING

This role is written for a sandbox environment and needs to be tweaked for other
environments.

# Please refer to the defaults/sample-all and defaults/sample-project vars file
# for enabling the roles system/service inputs

#### To Enable nginx logs, enable custom formatting in /etc/nginx/conf.d
```
# Custom logstash format
log_format logstash '$http_host '
                    '$remote_addr [$time_local] '
                    '"$request" $status $body_bytes_sent '
                    '"$http_referer" "$http_user_agent" '
                    '$request_time '
                    '$upstream_response_time';

```
#### Modify the nginx log config to use custom format
```
#access_log /var/log/nginx/access.log;
access_log /var/log/nginx/access.log logstash;
```

#### Various Environments Logging End Point
`loginfra.<ENV>.cloud.local - dev2/test2/preprod2/prod2`
