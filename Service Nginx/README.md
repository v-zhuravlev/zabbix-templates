Nginx https service monitoring template using zabbix active agent items and master item data obtained from by default http://localhost/stub_status.

Default addres of the stub_status page can be custimized by change macros values used by template:

| Macro              | Default value       | Description                                         |
| ------------------ | ------------------- | --------------------------------------------------- |
| {$NGINX_HOST}      | localhost           | Hostname of the nhings service                      |
| {$NGINX_PORT}      | 80                  | TCP port                                            |
| {$NGINX_STATS_URI} | /stub_status        | URI adderss of the status_stub page                 |
| {$NGINX_USER}      | nginx               | nginx non-root user used by workers nginx processes |

Version: 1.0.0 (WIP)

Changelog:
- 1.0.0 (WIP):
  - Initial version

Notes:
- This template uses nginx stub_status loadable module metrics
- To allow use this template in nginx.conf configuration file must be present in nginx.config:
```
    location /nginx_status {
	stub_status	on;
	# do not log query for stats in access log
	access_log	off;
	allow		127.0.0.1;
	deny		all;
    }
```