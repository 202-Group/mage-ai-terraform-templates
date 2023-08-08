# mage-ai-terraform-templates
Terraform templates for deploying mage-ai to AWS, GCP and Azure

# First time deploy to AWS ECS (production)
[mage instructions](https://docs.mage.ai/production/deploying-to-cloud/aws/setup)

1. `git clone https://github.com/202-Group/mage-ai-terraform-templates.git`
2. make sure your IAM account has these permissions
   - [terraform apply](https://docs.mage.ai/production/deploying-to-cloud/aws/terraform-apply-policy)
   - [terraform destroy](https://docs.mage.ai/production/deploying-to-cloud/aws/terraform-destroy-policy)
3. Drop AWS config and credentials files into `.aws` folder or configure aws cli
4. Terraform plan
   - You can run the following command to see all the resources that will be created by Terraform:
   ```
   cd aws
   terraform plan
   ```
    By default, here are the [resources](https://docs.mage.ai/production/deploying-to-cloud/aws/resources) that will be created.
5. ```terraform init```
6. ```terraform apply```
7. While we do want to commit our terraform configuration to git, 
we dont want to commit sensitive cloud resource info contained in the `terraform.tfstate` file. in order to maintain state 
and be able to destroy the resources if needed, we will copy to s3
```
cd ...
zip -r mage-ai-terraform-templates_20230808.zip ./mage-ai-terraform-templates
aws s3 cp mage-ai-terraform-templates_20230808.zip s3://bvgs-git/state/mage-initial-deploy/
```


Additional resources:
- [mage docs](https://docs.mage.ai/introduction/overview)



