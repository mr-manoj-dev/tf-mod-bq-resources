# tf-mod-bq-resources
Terraform to provision BigQuery resources like datasets and tables 



```shell
export PROJECT_ID="<gcp_project_id>"
export LOCATION="<location>"
export TF_STATE_BUCKET="<gcp_storage_bucket_name>"
export TF_STATE_PREFIX="<terraform_state_prefix>"
export WORKSPACE="test_workspace"
export INFRA_ROOT_FOLDER="infra"
export MODULE_NAME="datasets_and_tables"
export GOOGLE_PROVIDER_VERSION="= 4.47.0"
```


### Terraform plan: without workspace(Default shall be used)

```shell
gcloud builds submit \
    --project=$PROJECT_ID \
    --region=$LOCATION \
    --config terraform-plan-modules.yaml \
    --substitutions _TF_STATE_BUCKET=$TF_STATE_BUCKET,_TF_STATE_PREFIX=$TF_STATE_PREFIX,_WORKSPACE=,_INFRA_ROOT_FOLDER=$INFRA_ROOT_FOLDER,_MODULE_NAME=$MODULE_NAME,_GOOGLE_PROVIDER_VERSION=$GOOGLE_PROVIDER_VERSION \
    --verbosity="debug" .
```

#### Validate the logs to verify resources that are going to be add/change/destroy
```textmate
Plan: 4 to add, 0 to change, 0 to destroy.
─────────────────────────────────────────────────────────────────────────────

Saved the plan to: tfplan.out

```

### Now Run Terraform apply : without workspace(Default shall be used)

```shell
gcloud builds submit \
    --project=$PROJECT_ID \
    --region=$LOCATION \
    --config terraform-apply-modules.yaml \
    --substitutions _TF_STATE_BUCKET=$TF_STATE_BUCKET,_TF_STATE_PREFIX=$TF_STATE_PREFIX,_WORKSPACE=,_INFRA_ROOT_FOLDER=$INFRA_ROOT_FOLDER,_MODULE_NAME=$MODULE_NAME,_GOOGLE_PROVIDER_VERSION=$GOOGLE_PROVIDER_VERSION \
    --verbosity="debug" .
```

#### Verify logs you will found some logs ends with below which tells you what the apply command have reflected(add/change/destroy) to your resources

```textmate
Apply complete! Resources: 4 added, 0 changed, 0 destroyed.
PUSH
DONE

```
