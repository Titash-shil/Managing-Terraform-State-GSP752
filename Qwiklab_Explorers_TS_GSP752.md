# Managing Terraform State || [GSP752](https://www.cloudskillsboost.google/course_templates/505/labs/361054)

# # Like, comment, share & Don't forget to subscribe [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN) 👍😄🤝

### Run the following Commands in CloudShell

```
export REGION=
```
```
cat > main.tf <<EOF_END

provider "google" {
  project     = "$DEVSHELL_PROJECT_ID"
  region      = "$REGION"
}
resource "google_storage_bucket" "test-bucket-for-state" {
  name        = "$DEVSHELL_PROJECT_ID"
  location    = "US"
  uniform_bucket_level_access = true
}

terraform {
  backend "local" {
    path = "terraform/state/terraform.tfstate"
  }
}
EOF_END


terraform init

terraform apply --auto-approve


cat > main.tf <<EOF_END

provider "google" {
  project     = "$DEVSHELL_PROJECT_ID"
  region      = "$REGION"
}
resource "google_storage_bucket" "test-bucket-for-state" {
  name        = "$DEVSHELL_PROJECT_ID"
  location    = "US"
  uniform_bucket_level_access = true
}

terraform {
  backend "gcs" {
    bucket  = "$DEVSHELL_PROJECT_ID"
    prefix  = "terraform/state"
  }
}
EOF_END


yes | terraform init -migrate-state


gsutil label ch -l "key:value" gs://$DEVSHELL_PROJECT_ID

```

# Congratulations ..!!🎉  You completed the lab shortly..😃💯

# *Well done..!* 👏

# Thank you for visiting.... :) 🗯️

# [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN)
