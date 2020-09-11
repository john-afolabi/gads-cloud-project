## Task 1: Creating a Compute Engine Virtual Machine Instance

```
gcloud beta compute --project=qwiklabs-gcp-03-90fad43fb450 instances create dev-instance --zone=us-central1-a --machine-type=e2-medium --subnet=default --network-tier=PREMIUM --maintenance-policy=MIGRATE --service-account=762175782007-compute@developer.gserviceaccount.com --scopes=https://www.googleapis.com/auth/cloud-platform --tags=http-server --image=debian-10-buster-v20200910 --image-project=debian-cloud --boot-disk-size=10GB --boot-disk-type=pd-standard --boot-disk-device-name=dev-instance --no-shielded-secure-boot --no-shielded-vtpm --no-shielded-integrity-monitoring --reservation-affinity=any



gcloud compute --project=qwiklabs-gcp-03-90fad43fb450 firewall-rules create default-allow-http --direction=INGRESS --priority=1000 --network=default --action=ALLOW --rules=tcp:80 --source-ranges=0.0.0.0/0 --target-tags=http-server
```

## Task 2: Install software on the VM instance

```
gcloud beta compute ssh --zone "us-central1-a" "dev-instance" --project "qwiklabs-gcp-03-90fad43fb450"
```

```
sudo apt-get update
```

```
sudo apt-get install git
```

```
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
```

```
sudo apt install nodejs
```

## Task 3: Configure the VM to Run Application Software

```
node -v
```

```
git clone https://github.com/GoogleCloudPlatform/training-data-analyst
```

```
cd ~/training-data-analyst/courses/developingapps/nodejs/devenv/
```

```
sudo node server/app.js
```

```
npm install
```

```
node list-gce-instances.js
```
