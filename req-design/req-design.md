AWS documentation notes
=======================
Environment sharing best practices
We recommend the following practices when sharing environments.
• Only invite read/write members you trust to your environments.
• For EC2 environments, read/write members can use the environment owner's AWS access credentials, instead of their own credentials, to make calls from the environment to AWS services. To prevent this, the environment owner can disable AWS managed temporary credentials for the environment. However, this also prevents the environment owner from making calls. For more information, see AWS Managed Temporary Credentials.
• Turn on AWS CloudTrail to track activity in your environments. For more information, see the AWS CloudTrail User Guide.
• Do not use your AWS account root user to create and share environments. Use IAM users in the account instead. For more information, see First-Time Access Only: Your Root User Credentials and IAM Users in the IAM User Guide.

<br>

A shared environment in AWS Cloud9 offers three environment member access roles: owner, read/write, and read-only. <br>
<li>An owner has full control over an environment. </li>
<li>A read/write member</li>
<li>A read-only member</li>

<br>

Before a user can become an environment owner or member, that user must meet one of the following criteria. <br>
<li>• The user is an AWS account root user. </li>
<li>• The user is an IAM administrator user. For more information, see Creating Your First IAM Admin User and Group in the IAM User Guide. </li>
<li>• The user is a user who belongs to an IAM group, a user who assumes a role, or a federated user who assumes a role, and that group or role has the AWS managed policy AWSCloud9Administrator or AWSCloud9User (or AWSCloud9EnvironmentMember, to be a member only) attached. For more information, see AWS Managed (Predefined) Policies. </li>
<li>• To attach one of the preceding managed policies to an IAM group, you can use the AWS Management Console or the AWS Command Line Interface (AWS CLI) as described in the following procedures. </li>
<li>• To create a role in IAM with one of the preceding managed policies for a user or a federated user to assume, see Creating Roles in the IAM User Guide. To have a user or a federated user assume the role, see coverage of assuming roles in Using IAM Roles in the IAM User Guide. </li>

<br>
The type of environment member permissions associated with this environment member. Available values include:
<li> owner : Owns the environment. </li>
<li> read-only : Has read-only access to the environment. </li>
<li> read-write : Has read-write access to the environment. </li>

<hr>
================Option-1================= <br>
1.Project-AWSCloud9_Administrator  <br>
2.Project-Java-AWSCloud9_SuperUser <br>
3.Project-Java-AWSCloud9_EnvironmentMember <br>
4.Project-DotNet-AWSCloud9_SuperUser <br>
5.Project-DotNet-AWSCloud9_EnvironmentMember <br>
6.Project-NodeJs-AWSCloud9_SuperUser <br>
7.Project-NodeJs-AWSCloud9_EnvironmentMember <br>
8.Project-Terraform-AWSCloud9_SuperUser <br>
9.Project-Terraform-AWSCloud9_EnvironmentMember <br>

=================Option-2=================== <br>
1.Project-AWSCloud9_Administrator <br>
2.Project_AWSCloud9_SuperUser <br>
3.Project-Java-AWSCloud9_EnvironmentMember <br>
4.Project-DotNet-AWSCloud9_EnvironmentMember <br>
5.Project-NodeJs-AWSCloud9_EnvironmentMember	<br>
6.Project-Terraform-AWSCloud9_EnvironmentMember <br>


PROJECTDEV has choosen the Option-2 <br>
==================================== <br>
<ul> 1. Admin:      INAW_PROJECTDEV_Cloud9_Admin </ul>
<ul> 2. Superusers: INAW_PROJECTDEV_Cloud9_SuperUser </ul>
<ul> 3. Java :      INAW_PROJECTDEV_Cloud9_Java_EnvironmentMember </ul>
<ul> 4. DotNet :    INAW_PROJECTDEV_Cloud9_Dotnet_EnvironmentMember </ul>
<ul> 5. NodeJs :    INAW_PROJECTDEV_Cloud9_Nodejs_EnvironmentMember </ul>
<ul> 6. Terraform : INAW_PROJECTDEV_Cloud9_Terra_EnvironmentMember </ul

<br>

View Environments: <br>
=================== <br>
sureshadapa@localhost ~ % aws cloud9 list-environments <pre>
{
    "environmentIds": [
        "3106-DotNet-Env",
        "44bb-Java-Env", 
        "ea4b-NodeJs-Env" 
        "65d0-Terraform-Env",
    ]
} </pre>

https://ap-south-1.console.aws.amazon.com/cloud9/ide/3106-DotNet-Env <br>
https://ap-south-1.console.aws.amazon.com/cloud9/ide/44bb-Java-Env <br>
https://ap-south-1.console.aws.amazon.com/cloud9/ide/ea4b-NodeJs-Env <br>
https://ap-south-1.console.aws.amazon.com/cloud9/ide/65d0-Terraform-Env <br>


sureshadapa@localhost ~ % aws cloud9 describe-environment-memberships --environment-id 44bb-Java-Env <pre>
{
    "memberships": [
        {
            "permissions": "owner",
            "userId": "AROAZLKQUYOUT4XKDGOGS:suresh.adapa@abclabs.com",
            "userArn": "arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Admins_155fdce27cc31ea7/suresh.adapa@abclabs.com",
            "environmentId": "44bb-Java-Env",
            "lastAccess": "2023-01-09T14:27:37+05:30"
        }
    ]
}
</pre>
<br>
<pre>
User: arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Admin_b33f/suresh.adapa@abclabs.com
Service: iam
Action: GetAccountSummary
On resource(s): *
Context: no identity-based policy allows the iam:GetAccountSummary action

On Feb 06 2023
User: arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Admins_155fdce27cc31ea7/suresh.adapa@abclabs.com
</pre>
<hr>

===TASKS=== <br>
<pre>
1)
Group Description:- Who can create different environments like Java-Env, Dotnet-Env, Nodejs-Env,Python-Env,Clojure-Env
Group Name: INAW_PROJECTDEV_Cloud9_Administrator
Permissions / Policy Name: AWSCloud9Administrator
Members:-
ranga.prasad@abclabs.com
sivashankar.t@abclabs.com

Policy ARN: arn:aws:iam::aws:policy/AWSCloud9Administrator
Policy Usage: AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Admin_b33f
Role ARN: arn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Admin_b33f

Added On Feb 02 2023 :
arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Admin_b33f/ranga.prasad@abclabs.com
arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Admin_b33f/sivashankar.t@abclabs.com

</pre>
<hr>
<pre>
2)
Group Description:- Who can alter specific environment like Java-Env
Group Name: INAW_PROJECTDEV_Cloud9_Java_SuperUser
Permissions / Ploicy Name: AWSCloud9JavaSuperUser
Members:-
dinesh.c@abclabs.com
gourav.chhabra@abclabs.com
Can perform: RW
3)
Group Description:- Who can alter specific environment like Dotnet-Env
Group Name: INAW_PROJECTDEV_Cloud9_Dotnet_SuperUser
Permissions / Ploicy Name: AWSCloud9DotnetSuperUser
Members:-
dinesh.c@abclabs.com
gourav.chhabra@abclabs.com
Can perform: RW
4)
Group Description:- Who can alter specific environment like Nodejs-Env
Group Name: INAW_PROJECTDEV_Cloud9_Nodejs_SuperUser
Permissions / Ploicy Name: AWSCloud9NodeJsSuperUser
Members:-
dinesh.c@abclabs.com
gourav.chhabra@abclabs.com
Can perform: RW
5)
Group Description:- Who can alter specific environment like Terraform-Env
Group Name: INAW_PROJECTDEV_Cloud9_Terraform_SuperUser
Permissions / Ploicy Name: AWSCloud9TerraformSuperUser
Members:-
somil.g@abclabs.com
dinesh.c@abclabs.com
gourav.chhabra@abclabs.com
Can perform: RW
</pre>
<hr>
<pre> Consolidating all to one SuperUser - organisation choice
<b> 2+3+4+5) </b>
Group Description:- Who can alter specific environment
Group Name: INAW_PROJECTDEV_Cloud9_SuperUser
Permissions / Ploicy Name: AWSCloud9SuperUser
Members:-
dinesh.c@abclabs.com
gourav.chhabra@abclabs.com
somil.g@abclabs.com
Can perform: RW

Policy ARN: arn:aws:iam::aws:policy/AWSCloud9SuperUser
Policy Usage: AWSReservedSSO_INAW_PROJECTDEV_Cloud9_SuperUser_31a5
Role ARN: arn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_SuperUser_31a5

Added On Feb 06 2023 :
arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_SuperUser_31a5/dinesh.c@abclabs.com
arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_SuperUser_31a5/gourav.chhabra@abclabs.com
arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_SuperUser_31a5/somil.g@abclabs.com
</pre>
<hr>

<pre>
6)
Group Description: Project Java developers list
Group Name: INAW_PROJECTDEV_Cloud9_Java_EnvironmentMember
Permissions / Policy Name: AWSCloud9EnvironmentMember
Members:- AWSCloud9EnvironmentMember
muralidharan.s@abclabs.com
joshi.chandran@abclabs.com
anurag.dixit@abclabs.com
jyothiswaroop.rajan@abclabs.com
Can perform: RW

 
Policy ARN: arn:aws:iam::aws:policy/AWSCloud9EnvironmentMember
Policy Usage / Role ARN ?
arn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_NodejsEnvM_be13
* arn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Java_EnvM_d71b
arn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_.net_EnvM_f8d2
arn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Terra_EnvM_b1f2

Added On Feb 07 2023 :
arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Java_EnvM_d71b/muralidharan.s@abclabs.com
arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Java_EnvM_d71b/joshi.chandran@abclabs.com
arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Java_EnvM_d71b/anurag.dixit@abclabs.com
arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Java_EnvM_d71b/jyothiswaroop.rajan@abclabs.com
</pre>
<hr>

<pre>
7)
Group Description: Project Dotnet developers list
Group Name: INAW_PROJECTDEV_Cloud9_Dotnet_EnvironmentMember
Permissions / Ploicy Name: AWSCloud9EnvironmentMember
Members:-AWSCloud9EnvironmentMember
alfishan.ahmad@abclabs.com
baljeet.singh@abclabs.com
Can perform: RW

Policy Usage / Role ARN ?
arn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_NodejsEnvM_be13
arn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Java_EnvM_d71b
* arn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_.net_EnvM_f8d2
arn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Terra_EnvM_b1f2

Added On Feb 07 2023 :
arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_.net_EnvM_f8d2/alfishan.ahmad@abclabs.com
arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_.net_EnvM_f8d2/baljeet.singh@abclabs.com
</pre>
<hr>

<pre>
8)
Group Description: Project Nodejs developers list
Group Name: INAW_PROJECTDEV_Cloud9_Nodejs_EnvironmentMember
Permissions / Ploicy Name: AWSCloud9EnvironmentMember
Members:-AWSCloud9EnvironmentMember
mohit.sharma02@abclabs.com
shubham.sharma@abclabs.com
rishiab.r@abclabs.com
prashanth.jadhav@@abclabs.com
Can perform: RW

Policy Usage / Role ARN?
* arn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_NodejsEnvM_be13
arn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Java_EnvM_d71b
parn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_.net_EnvM_f8d2
parn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Terra_EnvM_b1f2

Added On Feb 07 2023 :
arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_NodejsEnvM_be13/mohit.sharma02@abclabs.com
arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_NodejsEnvM_be13/shubham.sharma@abclabs.com
arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_NodejsEnvM_be13/rishiab.r@abclabs.com
arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_NodejsEnvM_be13/prashanth.jadhav@abclabs.com
</pre>
<hr>

<pre>
9)
Group Description: Project Terraform developers list
Group Name: INAW_PROJECTDEV_Cloud9_Terraform_EnvironmentMember
Permissions / Ploicy Name: AWSCloud9EnvironmentMember
Members:-AWSCloud9EnvironmentMember
somil.g@abclabs.com
yogesh.p@abclabs.com
Can perform: RW

Policy Usage / Role ARN?
arn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_NodejsEnvM_be13
arn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Java_EnvM_d71b
parn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_.net_EnvM_f8d2
* parn:aws:iam::AWS-ACCOUNTID:role/aws-reserved/sso.amazonaws.com/ap-south-1/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_Terra_EnvM_b1f2


arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_NodejsEnvM_be13/somil.g@abclabs.com
arn:aws:sts::AWS-ACCOUNTID:assumed-role/AWSReservedSSO_INAW_PROJECTDEV_Cloud9_NodejsEnvM_be13/yogesh.p@abclabs.com
</pre>
<br>
============================
aws sts get-caller-identity <br>

Get inputs from respective PM's and add users/developer to respective groups and environments. <br>
Enjoy and Collobrate and have fun on cloud-9
