## Container Creation for Mongodb

- if you want to customize your mongodb version, just change `image: 'mongo:latest'` change latest to the version that you want

#### Mongodb Volumes
- by default, this script will create new volumes on host system named mongod_data. This volumes is managed by docker

#### Persisting data to storage
- Don't affraid for losing your data. It can be persisted to external storage or you can store it on your local container host.

by adding : `- {path-to-data}:/bitnami/mongodb` on volumes

- Note: last time i use images from `mongo:latest` , errors happened when try to mount volumes. i changed image sources to `bitnami/mongodb`to make it works