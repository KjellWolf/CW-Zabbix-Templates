# Installing and using this Template## Installing a Zabbix Template and Configuring Macros

## Step 1: Download and Import Zabbix Template

1. Download the Zabbix template from here.
2. Open the Zabbix dashboard in your web browser and navigate to `Configuration` => `Templates`.
3. Click on the `Import` button.
4. In the import page, choose the Zabbix template file you just downloaded.
5. Click on the `Import` button again to finish importing the template.

## Step 2: Fill out Macros

This Template is made to be added to the individual MinIO Hosts. 

### Getting the MinIO Prometheus Access Key
1. Setup the CLI tool `Minio Admin Client` like in the docs (https://min.io/docs/minio/linux/reference/minio-mc-admin.html)
2. The Access key will be the same for the whole cluster. So this will be needed once per cluster.
3. Run the following command `mc admin config get [alias] prometheus`


### Filling out the Macros
1. Open The host in Zabbix
2. Go To The tab `Macros` => `Inherited and host macros`
3. Fill out the following macro fields with the appropriate values:

- `{$MINIO.DNS.NAME}`           (MinIO Nodename | For Node Specific metrics | based on `node{1...4}.example.net`)
- `{$MINIO.DNS.WILDCARD}`       (Default: node* | Based on the upper ULR structure Too) 
- `{$S3.DRIVES.PER.ERASURE.SET}`(Default: 16 ) 
- `{$S3.MINIO.ACCESS.KEY}`      (Prometheus Endpoint Key)
- `{$S3.MINIO.API.URL}`         (The Prometheus endpoint Url . Can be the Load-balancer )
- `{$S3.MINIO.MAX.DEAD.DRIVES}` (**Note**: Legacy not needed)
- `{$S3.MINIO.PARITY}`          (Default: 4)