## Terraform for GCP

This provide VPC, GCE, health-check), loadbalancer(http), CloudSQL(MySQL,PostgreSQL).
CloudSQL is stored into private network (Do not use public IP Address).
<br>

## Preconditions

### API

You have to enable below API's via IAM.

- API enable
- Cloud Resource Manager API
- Cloud SQL Admin API

## Create Service account

#### Create Service attoung for Terraform
1. Move to [IAM & ADMIN] - [Service accounts]
2. Press the [CREATE SERVICE ACDCOUNT]
3. Enter the below valud in [Service account details] and press [CREATE].
    - Service account name: gcp-terraform (example)
    - Service account description：　for terraform (example)
4. Select below roles in [Service account permissions (optional) ] and press [CONTINUE]
    - Editor(project) , Service Networking Admin (Service Networking)
5. Attache the permmsion to service account in [Grant users access to this service attoun (optional)] and press [DONE]
    - Do not forget to create "CREATE KEY", that uses Terraform execution.


## Create Cloud Storage

1. Upload the Terraform state file to cloud storage.

```bash
# multi regional
gsutil mb -p <projectname> -c multi_regional -l Asia gs://mcmpj/

# regional
gsutil mb -p <projectname> -c regional -l asia-northeast1 gs://mcmpj/
```

2. Backet for upload file of MCM (documents related to contract).

```bash
$ gsutil ls
gs://${env}-Mcm-uploads/
```

Using GCS as a data storage via gcsfuse.


## Terraform Installation

### Terraform installation using `tfenv`

1. Clone sources from github and setting PATH.

```bash
git clone https://github.com/tfutils/tfenv.git ~/.tfenv
echo 'export PATH="$HOME/.tfenv/bin:$PATH"' >> ~/.bash_profile
source ~/.bash_profile
```

2. Checking terraform version which we can use.

```bash
tfenv list-remote
```

3. Installing rtfenv with specific version.

```bash
$ tfenv install 0.12.6
$ tfenv list
* 0.12.6 (set by /home/rao/.tfenv/version)
```

You already have some repository for terraform, please check whether `.terraform-version` file exist or not.
If you have `.terraform-version`, you can povide same Terraform version which is commited.

```bash
$ ls .terraform-version
.terraform-version
$ cat .terraform-version
0.12.6
$ tfenv install
$ tfenv list
* 0.12.6
```

## Terraform command

- When Provide resources

```bash

terraform fmt
terraform init
terraform validate
terraform plan
terraform apply
```

- when delete resources

```bash
terraform plan -destroy
terraform deestroy
```
