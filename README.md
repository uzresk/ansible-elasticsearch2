# set up Elasticsearch2.x

set up EFK(elasticsearch + fluentd + kibana)

## Provides

* java8
* elasticsearch

## Requires

1. Ansible(checked 1.9.1)
2. CentOS 6.5 later

## Usage

### Get the code
`$ git clone https://github.com/uzresk/ansible-elasticsearch.git`

### change hosts file 

	[server]  
	192.168.1.20  

### setting /roles/elasticsearch/vars/main.yml

```
elasticsearch_configs:
  dl_url: https://download.elasticsearch.org/elasticsearch/release/org/elasticsearch/distribution/rpm/elasticsearch/2.1.1/elasticsearch-2.1.1.rpm
  rpm_path: /usr/local/src/elasticsearch-2.1.0.rpm
  cluster_name: test-cluster
  node_name: ${HOSTNAME}
  network_host: '_eth1:ipv4_'
  path_data: /var/lib/elasticsearch/
  path_logs: /var/log/elasticsearch/
  bootstrap_mlockall: "true"
  init_params:
    - { regexp: 'export ES_HEAP_SIZE', line: 'export ES_HEAP_SIZE=512m' }
    - { regexp: 'export ES_JAVA_OPTS', line: 'export ES_JAVA_OPTS="-Djava.rmi.server.hostname=192.168.1.41 -Dcom.sun.management.jmxremote=true -Dcom.sun.management.jmxremote.port=7085 -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.authenticate=false"' }
  discovery_unicast_host: ["192.168.1.41:9300", "192.168.1.42:9300"]
  minimum_master_nodes: 1
#  proxy_host: proxyhost
#  proxy_port: 8080
  plugins:
    - { name: 'analysis-kuromoji', location: 'analysis-kuromoji' }
    - { name: 'head', location: 'mobz/elasticsearch-head' }
```

### Run the Playbook

`$ ansible-playbook -i hosts site.yml`

## License

MIT

## Author

[uzresk](https://github.com/uzresk)

