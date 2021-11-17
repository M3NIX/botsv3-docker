# botsv3-docker

## setup
1. Go to `https://splunkbase.splunk.com/app/1809/` and download the addon in version `7.1.3`. Save it in the data folder. 
2. Run the following commands
```
wget https://botsdataset.s3.amazonaws.com/botsv3/botsv3_data_set.tgz -P data/
mkdir apps && for f in data/*.tgz; do tar -xf "$f" -C ./apps/; done
sudo docker build . -t botsv3
sudo docker run -d -p 8000:8000 -e "SPLUNK_START_ARGS=--accept-license" -e "SPLUNK_PASSWORD=changeme" --name botsv3 botsv3
```
3. You can now reach your BOTS v3 Splunk instance at `http://localhost:8000/` and login as `admin:changeme`.

The BOTS v3 data will be available by searching:
```
index=botsv3 earliest=0
````
