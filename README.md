## Survey and Improvement of Distributed Machine Learning onSpark

### Instruction for artifact evaluation

Follow the instruction below on how to launch a Jupyternote book and add this repository to AWS SageMaker.

Experiments could be found at 

- Notebook/ParameterServer.ipynb
- Notebook/Horovod.ipynb


### Steps for launching Jupyter Notebook:

#### Select one of the following AWS Regions in your AWS console:
![Navigate to Sagemaker Service](/images/image-20.png)


#### Open SageMaker Console by clicking on "Services" and searching for Sagemaker
![Navigate to Sagemaker Service](/images/image-1.png)



#### Navigate to SageMaker Notebooks
![Navigate to Sagemaker Notebooks](/images/image-2.png)



#### Create a SageMaker Notebook Instance
![Creae Sagemaker Notebooks](/images/image-3.png)


#### Give the SageMaker Notebook Instance a name (note that '_' are not allowed). 
#### From the drop-down menu, select a compute instance type for your Jupyter Notebook. We recommend 'ml.t2.medium' for lowest cost.
![Name Sagemaker Notebooks](/images/image-21.png)

#### In 'Permissions and encryption' pane click on "Create a new role".
![Name Sagemaker Notebooks](/images/image-4.png)

#### Select "Any S3 bucket" and click on "Create role"
![Create IAM role for Sagemaker](/images/image-5.png)

#### You will see a newly created IAM SageMaker role
![Create IAM role for Sagemaker](/images/image-6.png)

#### We now need to add a few more security policies to our newly created IAM SageMaker role.

#### Click on newly created IAM SageMaker role

#### Click on "Attach Policies" button
![Create IAM role for Sagemaker](/images/image-22.png)

#### Search for "EC2Container" and add AmazonEC2ContanerRegistryFullAccess policy (click on the radio button to the left)
![Create IAM role for Sagemaker](/images/image-7.png)



#### Search for "VPC" and add AmazonVPCAccess policy (click on the radio button to the left)
![Create IAM role for Sagemaker](/images/image-8.png)



#### Click on "Attach Policies" button. Your policy list for the SageMaker IAM role should look like this:
![Create IAM role for Sagemaker](/images/image-9.png)



#### We need a custom policy to allow full access to CloudFormation service. 
"Add in-line policy". Select JSON tab and paste the following:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": "cloudformation:*",
            "Resource": "*"
        }
    ]
}
```


![Create IAM role for Sagemaker](/images/image-10.png)

#### Give your policy a name and click on "Create Policy"
![Create IAM role for Sagemaker](/images/image-11.png)



#### Your policy list for the SageMaker IAM role should look like this:
![Create IAM role for Sagemaker](/images/image-12.png)



#### Switch to the previous browser tab with SageMaker Notebook (you may close browser tab with IAM service), scroll down to "Git Repositories", click on "Repository" and select "Add Repository to Amazon SageMaker"
![Create IAM role for Sagemaker](/images/image-13.png)



#### Select 'repository icon', give it a name, past repo's URL (https://github.com/aws-samples/sagemaker-horovod-distributed-training) and click on "Add repository"
![Create IAM role for Sagemaker](/images/image-14.png)



#### If successful, you will see the Git repo listed under SageMaker Git Repositories:
![Create IAM role for Sagemaker](/images/image-15.png)


#### You can now close this browser's tab and go back to the previous tab where we were creating the notebook. Click on "refresh" button on Git Repositories pane. The github repo's name should now be available in the drop-down list. Select it and click on "Create Notebook Instance" at the bottom of the page.
![Create IAM role for Sagemaker](/images/image-16.png)



#### You will see your notebook in "Pending" status. It will take a few minutes for the Jupyter Server to start up and clone your repo. When the status changes to "InService", click on "Open Jupyter" next to the status.
![Create IAM role for Sagemaker](/images/image-17.png)

 

This work is based on two SageMaker examples available in AWS SageMaker Examples directory:
- https://github.com/awslabs/amazon-sagemaker-examples/tree/master/sagemaker-python-sdk/tensorflow_script_mode_training_and_serving
and
- https://github.com/awslabs/amazon-sagemaker-examples/tree/af765120763364193f099af0b283767cc2228ad3/sagemaker-python-sdk/tensorflow_script_mode_horovod


## License

This library is licensed under the Apache 2.0 License. 
