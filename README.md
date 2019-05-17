# Sync networks from TF to router and configuring FRR and ifaces

Script can generate 2 kind of config file:
  1. For service chain mode of router
  2. For evpn mode of router

Script runs via cron, like that:
```bash
echo '*/1 * * * * /opt/tf_sync/vnc_sync' | crontab -u root -
```

Script use vnc_api python module. Now for install it you have to extract archive to root like that:
```bash
tar -xvf /opt/tf_sync/contrail-api-cli-*.tar -C /
```

For get vnc_api module you have to:
  * either build from source [VNC_API](https://github.com/Juniper/contrail-api-client.git)
  * or pack ready module from TF container (ex. contrail-controller-config-api). List of folders to pack:
     - sandesh_common-0.1dev-py2.7.egg-info
     - cfgm_common
     - contrail_api_client-5.1.0-py2.7.egg-info
     - ContrailCli-0.1-py2.7.egg-info
     - pysandesh
     - sandesh_common
     - vnc_api
     - sandesh-0.1dev-py2.7.egg-info
     - libpartition
     - ContrailCli
     - libpartition-0.1dev-py2.7.egg-info
     - cfgm_common-0.1dev-py2.7.egg-info

Example of tf_sync configs resides in etc/vnc_sync/*.example

Jinja2 templates in etc/vnc_sync/templates
