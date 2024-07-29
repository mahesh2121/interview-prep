
# Answers to DevOps and Related Questions

## 1. What is GIT stash?
GIT stash is a command in Git that allows you to temporarily save changes you have made to your working directory, so you can work on something else and come back to your changes later. It essentially stashes the modifications in a new stash entry on the stack, without committing them.

## 2. What is a branching strategy?
A branching strategy is a workflow or methodology that teams use to manage changes to the source code. Common strategies include:
- **Feature branching**: Each new feature is developed in its own branch.
- **Gitflow**: Uses feature branches, develop, and master branches with defined release and hotfix branches.
- **Trunk-based development**: Developers integrate small, frequent updates to the main branch.

## 3. What is the command to discard changes in the working directory?
To discard changes in the working directory in Git, you can use:
- `git checkout -- <file>`: Discards changes in a specific file.
- `git reset --hard`: Discards all changes in the working directory.

## 4. How do you debug the exited container?
To debug an exited Docker container:
1. Use `docker ps -a` to list all containers and find the container ID of the exited container.
2. Start the container in interactive mode: `docker start -i <container_id>`.
3. Alternatively, you can inspect logs using `docker logs <container_id>`.

## 5. How do you execute jobs in parallel in Jenkins?
To execute jobs in parallel in Jenkins, you can:
- Use the **Pipeline plugin** and define parallel stages within a `Jenkinsfile`:
```groovy
pipeline {
    stages {
        stage('Parallel Stage') {
            parallel {
                stage('Job 1') {
                    steps {
                        // Steps for Job 1
                    }
                }
                stage('Job 2') {
                    steps {
                        // Steps for Job 2
                    }
                }
            }
        }
    }
}
```

## 2. What is a branching strategy?
A branching strategy is a workflow or methodology that teams use to manage changes to the source code. It helps in organizing work and managing the integration of features, bug fixes, and releases. Common strategies include:

- **Feature branching**: Each new feature is developed in its own branch.
- **Gitflow**: Uses feature branches, develop, and master branches with defined release and hotfix branches.
- **Trunk-based development**: Developers integrate small, frequent updates to the main branch.

**Release Branch**: In addition to the common strategies mentioned above, **release branches** are used in some workflows to prepare for a new production release. They allow teams to stabilize the release by focusing on final bug fixes, performance improvements, and other pre-release tasks without affecting ongoing development in the main branch.

In **Gitflow**, the release branch is created from the develop branch. When the release is ready, the release branch is merged into both the main (master) branch and the develop branch, ensuring that any changes made during the release preparation are integrated back into the ongoing development.

**Release branches** help in:
- Finalizing features and fixes for the release.
- Stabilizing the release version without disrupting ongoing development.
- Allowing only critical fixes and release-related tasks.

## 6. Maven Lifecycle
Maven's build lifecycle consists of three built-in lifecycles: **default**, **clean**, and **site**.
- **default**: Handles project deployment, with phases like `validate`, `compile`, `test`, `package`, `verify`, `install`, and `deploy`.
- **clean**: Handles project cleaning, with phases like `pre-clean`, `clean`, and `post-clean`.
- **site**: Handles the creation of the project's site documentation, with phases like `pre-site`, `site`, and `post-site`.

## 7. How do you upgrade Jenkins?
To upgrade Jenkins:
1. Backup your current Jenkins configuration and data.
2. Download the new Jenkins war file from the official Jenkins website.
3. Replace the existing war file in your Jenkins installation directory.
4. Restart Jenkins to apply the upgrade.

## 8. What is a Parameterized Job in Jenkins?
A Parameterized Job in Jenkins is a job that allows you to pass parameters (input values) to the job at runtime. This is useful for making the job more flexible and reusable. You can define parameters in the job configuration and access them in the build steps.

## 9. What is Docker Swarm?
Docker Swarm is a native clustering and orchestration tool for Docker containers. It allows you to create and manage a cluster of Docker nodes as a single virtual system. It provides features like service discovery, load balancing, scaling, and desired state management.

## 10. How do you handle codes in Nexus satisfactorily?
To handle codes in Nexus satisfactorily:
- **Organize repositories**: Use separate repositories for different types of artifacts (e.g., releases, snapshots).
- **Access control**: Implement proper access controls and roles to restrict access.
- **Clean up old artifacts**: Set up scheduled tasks to remove old or unused artifacts.
- **Integration**: Integrate Nexus with your CI/CD pipeline to automatically publish and retrieve artifacts.

## 11. How do you manage space issues in the Jenkins server?
To manage space issues in the Jenkins server:
- **Regular cleanup**: Use the Disk Usage plugin to monitor disk usage and clean up old builds.
- **Limit build retention**: Configure jobs to retain only a certain number of builds.
- **Workspace cleanup**: Periodically clean up workspaces.
- **Archive artifacts**: Use external storage for build artifacts.
- **Dockerize**: Use Docker containers to isolate and manage build environments.

## 12. What is a multibranch project in Jenkins?
A Multibranch Project in Jenkins allows you to automatically manage branches in a repository. It detects new branches, creates jobs for them, and removes jobs when branches are deleted. This is useful for projects with multiple branches, as it automates the creation and management of jobs for each branch.

## 13. How do you secure the Jenkins server?
To secure the Jenkins server:
- **Enable security**: Use Jenkins' built-in security features.
- **User authentication**: Integrate with LDAP or other authentication mechanisms.
- **Role-based access control**: Use plugins like Role Strategy to define and enforce roles and permissions.
- **Use HTTPS**: Secure the Jenkins server with SSL/TLS.
- **Regular updates**: Keep Jenkins and its plugins up to date.
- **Audit logging**: Enable and monitor audit logs.

## 14. How do you manage GitHub roles?
To manage GitHub roles:
- **Repository roles**: Assign roles like Admin, Maintainer, and Contributor to control access levels.
- **Organization roles**: Define roles at the organization level to manage access to multiple repositories.
- **Teams**: Create teams within the organization to group users and manage permissions more easily.
- **Branch protection**: Use branch protection rules to enforce code review and other policies.

## 15. What is a NULL resource in Terraform?
A NULL resource in Terraform is a resource that allows you to execute arbitrary code or configurations that are not directly managed by Terraform. It can be used with the `null_resource` resource type and `provisioners` to run scripts, commands, or other tasks during the apply phase.


=========================================================================================================
# Questions and Answers

1. **What is called terraform fmt?**
   `terraform fmt` is a command used in Terraform to format Terraform configuration files to a canonical format and style. It helps maintain consistency in configuration files.

2. **What is called Snowball?**
   AWS Snowball is a data transfer service that uses secure devices to transfer large amounts of data into and out of AWS. It is typically used to move data when network transfer is impractical.

3. **How do you manage credentials in Terraform?**
   Credentials in Terraform can be managed using environment variables, a credentials file, or secrets management solutions. For AWS, credentials can be set using environment variables (`AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`) or through AWS CLI configuration files.

4. **What is called Code Deploy in AWS?**
   AWS CodeDeploy is a deployment service that automates code deployments to any instance, including Amazon EC2 instances and on-premises servers.

5. **Can you attach a single EBS volume to multiple EC2 instances at the same time?**
   No, a single EBS volume can only be attached to one EC2 instance at a time. To share data, you might use EFS (Elastic File System) or S3.

6. **Can you use Multiple FROM in DockerFile?**
   Yes, Docker supports multi-stage builds, where you can use multiple `FROM` statements to create multiple build stages in a single Dockerfile.

7. **DockerFile runs as which user?**
   By default, Dockerfile commands run as the `root` user. You can specify a different user using the `USER` instruction.

8. **How can we pass an argument to DockerFile?**
   You can pass arguments to a Dockerfile using the `ARG` instruction in the Dockerfile and then specifying values for these arguments with the `--build-arg` flag during the build.

9. **What are deployment strategies?**
   Deployment strategies are methods used to deploy software updates with minimal disruption. Common strategies include blue-green deployments, canary releases, rolling updates, and feature toggles.

10. **What is called an application load balancer?**
    An Application Load Balancer (ALB) is a type of load balancer in AWS that operates at the application layer (Layer 7) and can route traffic based on content and URL paths.

11. **What is Kubernetes architecture?**
    Kubernetes architecture consists of a cluster with master and worker nodes. The master node manages the cluster, while worker nodes run the applications. Key components include the API server, etcd, controller manager, scheduler, and kubelet.

12. **What is called Fargate service in AWS?**
    AWS Fargate is a serverless compute engine for containers that allows you to run Docker containers without managing the underlying infrastructure. It integrates with Amazon ECS and EKS.

13. **What are Register targets in Ansible?**
    Register targets in Ansible are variables where the output of a task is stored. You can use these variables later in the playbook.

14. **How do you pull artifacts from NEXUS?**
    Artifacts can be pulled from Nexus by configuring your build tool (e.g., Maven, npm, or Docker) to point to the Nexus repository and then using the tool's commands to fetch the artifacts.

15. **How to access the S3 bucket privately?**
    To access an S3 bucket privately, you can use IAM policies to control access, ensure that the bucket is not publicly accessible, and use VPC endpoints or private access configurations.

16. **What is the difference between a NAT instance and a NAT Gateway?**
    A NAT instance is an EC2 instance configured to provide network address translation, while a NAT Gateway is a managed AWS service with higher availability, scalability, and no need for maintenance.

17. **How can you restrict particular IPs accessing EC2 instances?**
    You can restrict IP access to EC2 instances using security groups and network ACLs to define rules that allow or deny traffic based on IP addresses.

18. **What is called VPC peering?**
    VPC peering is a networking connection between two VPCs that enables them to route traffic between each other using private IP addresses.

19. **What is called Transit Gateway?**
    AWS Transit Gateway is a service that enables you to connect multiple VPCs and on-premises networks through a central gateway, simplifying network management.

20. **What are the types of autoscaling?**
    The main types of autoscaling are horizontal scaling (adding or removing instances) and vertical scaling (increasing or decreasing the size of instances).

21. **To prevent DDOS attacks, which load balancer is used?**
    AWS Shield and AWS WAF (Web Application Firewall) can be used in conjunction with Elastic Load Balancer (ELB) to help prevent DDoS attacks.

22. **What is called a sticky session?**
    Sticky sessions, or session affinity, ensure that a user's requests are always sent to the same backend instance during a session. This can be configured using load balancers.

23. **What is called Lambda?**
    AWS Lambda is a serverless compute service that allows you to run code in response to events without provisioning or managing servers.

24. **How do you manage tfstate file in Terraform?**
    The `tfstate` file can be managed using remote state storage solutions such as AWS S3 with state locking provided by DynamoDB to handle state file consistency and backups.

25. **How do you create multiple EC2 instances in Terraform?**
    You can create multiple EC2 instances in Terraform using the `count` parameter in the `aws_instance` resource block to specify the number of instances.

26. **AWS has released a new service, how does Terraform behave?**
    Terraform may not immediately support new AWS services or features. You might need to update Terraform and its providers to gain support for newly released services.

27. **How do you uncommit the changes that have already been pushed to GitHub?**
    You can use `git revert` to create a new commit that undoes the changes, or `git reset` and force-push if you need to remove commits from history (caution: this can affect collaborators).

28. **What is the difference between git pull and git fetch?**
    `git fetch` downloads changes from the remote repository but does not merge them into your local branch. `git pull` fetches changes and automatically merges them into your local branch.

29. **What is called Jenkins File?**
    A Jenkinsfile is a text file that contains the definition of a Jenkins pipeline, using either Declarative or Scripted syntax, to automate the CI/CD process.

30. **What is called Shared Libraries in Jenkins?**
    Shared Libraries in Jenkins are reusable code or scripts that can be shared across multiple Jenkins pipelines, allowing for better modularity and maintenance.

31. **What is called Docker networking?**
    Docker networking refers to the various ways Docker containers communicate with each other and with the outside world, including bridge networks, host networks, and overlay networks.

32. **What is called a Trust relationship in AWS?**
    A trust relationship is a policy document in AWS IAM that defines which entities (users, services) are allowed to assume a role.

33. **What is called Public Subnet and Private Subnet?**
    A public subnet is a subnet whose traffic is routed to the internet via an internet gateway, while a private subnet is not directly accessible from the internet.

34. **How do you establish a connection between EC2 instances?**
    EC2 instances can connect to each other using private IP addresses if they are in the same VPC or via a VPN or Direct Connect if they are in different VPCs.

35. **What is realm command?**
    The `realm` command is used to manage Kerberos and LDAP-based domain configurations on Linux systems.

36. **How do you differentiate within an AWS account dev env, test env, and prod env?**
    You can differentiate environments using different VPCs, subnets, IAM roles, resource tags, or AWS accounts.

37. **Types of EC2 instances?**
    EC2 instances come in various families, including General Purpose (e.g., t3, m5), Compute Optimized (e.g., c5), Memory Optimized (e.g., r5), Storage Optimized (e.g., i3), and Accelerated Computing (e.g., p3).

38. **How can you encrypt an already created unencrypted EBS without creating a fresh EC2 instance?**
    You can create a snapshot of the unencrypted EBS volume, copy the snapshot with encryption enabled, and then create a new EBS volume from the encrypted snapshot.

39. **How do you install Nginx in the Ansible playbook?**
    You can use the `ansible.builtin.yum` or `ansible.builtin.apt` module to install Nginx in an Ansible playbook, depending on the package manager of the target system.

40. **How do you recover the deleted object in S3?**
    If versioning is enabled on the S3 bucket, you can recover the deleted object by accessing previous versions. If versioning is not enabled, you may need to rely on backup solutions or data recovery services.

41. **How do you route the data only to one EC2 instance when an application load balancer has 5 servers connected?**
    You can use routing rules or weighted target groups in the ALB to direct traffic to a specific instance.

42. **What is called “FROM SCRATCH” in Docker?**
    `FROM SCRATCH` is used in Dockerfiles to create a base image with no pre-installed libraries or dependencies, typically used for building minimalistic images.

43. **Can we run the container inside the container?**
    Yes, running containers inside containers is possible but generally not recommended. It can be achieved using Docker-in-Docker (DinD) or similar approaches.

44. **Can we use Ansible to create infrastructure in AWS?**
    Yes, Ansible can be used to create and manage infrastructure in AWS using modules like `ec2` and `ec2_asg` for instance and autoscaling group management.

45. **What is called EC2 auto recovery?**
    EC2 auto recovery is a feature that automatically recovers an instance when it becomes impaired due to an underlying hardware failure or other issues.

46. **What is called Persistent Storage in Docker?**
    Persistent storage in Docker refers to volumes that are designed to retain data even after the container is stopped or removed.

47. **What happens when you delete /var/lib/docker/overlay?**
    Deleting `/var/lib/docker/overlay` removes Docker’s overlay filesystem, which can lead to loss of data and container malfunction. It's crucial to ensure proper backup before performing such actions.

48. **What are called regular expressions in Linux?**
    Regular expressions (regex) are patterns used to match character combinations in strings. They are used in various tools and commands like `grep`, `sed`, and `awk`.

49. **What is called DynamoDB?**
    DynamoDB is a managed NoSQL database service provided by AWS that offers fast and predictable performance with seamless scalability.

50. **How do you push the image to DockerHub?**
    You push an image to DockerHub using the `docker push` command, after tagging the image with your DockerHub repository.

51. **Why do you change the name of the image using the tag command in Docker?**
    Tagging an image allows you to give it a more meaningful or versioned name and ensures it can be referenced and managed effectively in Docker repositories.

52. **How do you authorize data to the Application Load Balancer?**
    Data authorization to an ALB can be managed using security groups, IAM roles, and policies that define access permissions.

53. **What is called Event Handler in Lambda?**
    An event handler in AWS Lambda is a function that is triggered in response to an event, such as an S3 upload or a DynamoDB update.

54. **What is CloudFormation?**
    AWS CloudFormation is a service that allows you to define and provision AWS infrastructure using code in the form of templates.

55. **How do you change the name of an instance in Terraform file without destroying it?**
    You can change the instance name by modifying the `name` attribute in the Terraform configuration and then applying the changes. Terraform will handle the update without destroying the resource.

56. **How does Ansible execute the jobs?**
    Ansible executes jobs by connecting to target systems via SSH (or other connection methods) and running tasks defined in playbooks sequentially.

57. **How to connect the on-premise data center to AWS?**
    Connections can be established using AWS Direct Connect, VPN connections, or a hybrid cloud approach with services like AWS Storage Gateway.

58. **What is a GIT tag?**
    A Git tag is a reference to a specific point in Git history, often used to mark releases or important commits.

