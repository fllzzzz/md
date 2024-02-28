## version
## services
### build
- context (can be git-repository)
- dockerfile
- network
- args
- ...
### port
- HOST_PORT:CONTAINER_PORT
### network
- 父级配置
	```yaml
	# custom name
	frontend:
		driver: host
	backend:
		driver: bridge
		driver_opts:
		foo: "1"
		bar: "2"
	```
	- configuration ip address
	```yaml
	app_net:
		ipam:
		driver: default
		config:
			- subnet: "172.16.238.0/24"
			- subnet: "2001:3984:3989::/64"
	```
- 子级配置
	```yaml
	app:
		build: ./app
		networks:
		# is fist padding custom name
		- frontend
		- backend
	```
	- configuration ip address
	```yaml
	app_net:
			ipv4_address: 172.16.238.10
			ipv6_address: 2001:3984:3989::10
	```
### cgroup_parent `设置cg`

### command `覆盖容器启动后默认执行的命令`

### depends_on `启动依赖`

### devices `设备映射`
```yaml
devices:
  - "/dev/ttyUSB0:/dev/ttyUSB0"
```

###　links　`容器链接`

### restart 
no是默认的重启策略，在任何情况下都不会重启容器。当always指定时，容器总是重新启动。on-failure如果退出代码指示失败错误，则该策略会重新启动容器。unless-stopped总是重新启动容器，除非容器停止（手动或其他方式）。
`restart: unless-stopped`

###　sysctls 
```yaml
sysctls:
  net.core.somaxconn: 1024
  net.ipv4.tcp_syncookies: 0
```

### volumes

### container_name



