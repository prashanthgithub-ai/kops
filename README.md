# kops
kops is kubernetes operation ,kops multinode clusters
Kops can be created and manage the autoscaling and load balancers automatically
Create the server with ubuntu
* Select the ubuntu
* Select the t2 micro
* Increase the storage to 25
* Change to the root user
* Update the server apt update -y
  # insall the docker
  sudo apt install curl wget apt-transport-https -y
  sudo curl -fsSL https://get.docker.com -o get-docker.sh
  chmod 777 get-docker.sh
  sh get-docker.sh
  Start the docker by command systemctl start docker
  Status the docker by command systemctl status docker
  ![Screenshot 2024-11-20 131252](https://github.com/user-attachments/assets/c74518ad-bf65-4665-8d36-730a84c73d28)
     * Install the kubectl packages
    * go to aws configure
    * go to snap info aws-cli
    * go to snap install aws-cli --channel=v1/stable --classic to install the aws cli
    * Create user in iam and give access permissions to the user
      # install kops
      curl -LO https://github.com/kubernetes/kops/releases/download/v1.25.0/kops-linux-amd64
      chmod +x kops-linux-amd64
      mv kops-linux-amd64 /usr/local/bin/kops
      kops version
      mv kubectl /usr/local/bin/kubectl
      Go inside of the file vi .bashrc   
      ![Screenshot 2024-11-20 145723](https://github.com/user-attachments/assets/cba505e6-145f-45b0-bef6-d392dd25c95e)
      *save the file :wq!
      Type source .bashrc command
      #  IAM user
      go to aws confgiure
      acess by using acess key
      ![Screenshot 2024-11-20 201802](https://github.com/user-attachments/assets/1277bf77-e6a4-4390-a153-1a6f50b93604)
      # create bucket
      . Create the bucket by the cmd
      aws s3api create-bucket --bucket prash --region us-east-1
      . To enable the versioning by the cmd
      aws s3api put-bucket-versioning --bucket prash --regionus-east-1 --versioning-configuration Status=Enabled
    Exporting the bucket in kops by the command
    export kops_state_store=s3://prash
    # create the cluster
  to create cluster by the cmd
  kops create cluster --name raj.k8s.local --state=s3://prash --zones us-east-1a --master-size t2.medium --node-size t2.micro
  * It can create the s3 bucket, autoscaling, load balancer automatically in N.virginia as shown in below figure
  * ![Screenshot 2024-11-20 155049](https://github.com/user-attachments/assets/3c6e939a-c394-467d-824d-ad1b193c1075)
  * ![Screenshot 2024-11-20 160206](https://github.com/user-attachments/assets/05c4ff65-4236-47fc-97f7-46797c76347f)
# create yml file
vi pod.yml
![Screenshot 2024-11-20 193703](https://github.com/user-attachments/assets/7450b522-860d-4703-b989-c39e10165419)
give cmd kubectl get pods
![Screenshot 2024-11-20 194033](https://github.com/user-attachments/assets/992451db-7281-4897-b6a6-c085e5692abb)



