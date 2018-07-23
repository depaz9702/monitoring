docker-compose up -d influxdb
docker exec -ti pl17dublin_influxdb_1 influx
> CREATE USER "admin" WITH PASSWORD 'admin' WITH ALL PRIVILEGES;
docker exec -ti pl17dublin_influxdb_1 bash
> influx
>> auth
>> CREATE DATABASE prometheus;
>> CREATE USER "prom" with password 'prom';
>> GRANT ALL ON prometheus TO prom;
>> ALTER RETENTION POLICY "autogen" ON "prometheus" DURATION 1d REPLICATION 1 SHARD DURATION 1d DEFAULT;
>> SHOW RETENTION POLICIES ON prometheus;