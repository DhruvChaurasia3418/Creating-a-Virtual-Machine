# Set the project region for this lab
gcloud config set compute/region us-west1

# Create a variable for region
export REGION=us-west1

# Create a variable for zone
export ZONE=us-west1-c

# Create a new instance named "gcelab"
gcloud compute instances create gcelab \
  --zone=$ZONE \
  --machine-type=e2-medium \
  --image-project=debian-cloud \
  --image-family=debian-11 \
  --tags=http-server

# Create a firewall rule to allow HTTP traffic to instances with the "http-server" tag
gcloud compute firewall-rules create allow-http \
  --action=ALLOW \
  --direction=INGRESS \
  --rules=tcp:80 \
  --source-ranges=0.0.0.0/0 \
  --target-tags=http-server

# Create another instance named "gcelab2"
gcloud compute instances create gcelab2 \
  --machine-type=e2-medium \
  --zone=$ZONE

# SSH into the "gcelab" instance
gcloud compute ssh gcelab --zone=$ZONE --quiet
