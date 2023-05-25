[comment]: # "Auto-generated SOAR connector documentation"
# GitLab

Publisher: Peter Bertel  
Connector Version: 1\.0\.3 
Product Vendor: GitLab  
Product Name: GitLab  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 5\.3 

This app integrates with a GitLab instance to perform various lookups and execute CI/CD pipelines


# GitLab Phantom App

This app connects a GitLab instance with Splunk>Phantom instance. The GitLab App for Phantom allows
playbooks to implement various actions from the [GitLab
API](https://docs.gitlab.com/ee/api/api_resources.html) . File: readme.html Copyright (c) Peter
Bertel, 2020 Licensed under Apache 2.0 (https://www.apache.org/licenses/LICENSE-2.0.txt)


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a GitLab asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**gitlab\_location** |  required  | string | The Hostname or IP address of the GitLab instance
**personal\_access\_token** |  required  | password | Access token for a GitLab user

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration  
[list users](#action-list-users) - List all the users in the GitLab instance  
[list projects](#action-list-projects) - List all the projects in the GitLab instance  
[list branches](#action-list-branches) - List the branches of a GitLab project  
[create trigger](#action-create-trigger) - Create a new pipeline trigger for a GitLab project  
[list triggers](#action-list-triggers) - List the pipeline triggers of a GitLab project  
[run pipeline](#action-run-pipeline) - Execute a pipeline on a particular branch of a project  

## action: 'test connectivity'
Validate the asset configuration for connectivity using supplied configuration

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'list users'
List all the users in the GitLab instance

Type: **investigate**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.data | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 
action\_result\.data\.\*\.username | string |  `user name` 
action\_result\.data\.\*\.can\_create\_project | boolean |   

## action: 'list projects'
List all the projects in the GitLab instance

Type: **investigate**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 
action\_result\.data\.\*\.\*\.name | string | 
action\_result\.data\.\*\.\*\.path | string |   

## action: 'list branches'
List the branches of a GitLab project

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**project\_id** |  required  | The ID of the GitLab project | numeric |  `gitlab project id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.project\_id | numeric | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 
action\_result\.data\.\*\.name | string |   

## action: 'create trigger'
Create a new pipeline trigger for a GitLab project

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**project\_id** |  required  | The ID of the GitLab project | numeric |  `gitlab project id` 
**trigger\_name** |  required  | The name of the new trigger | string |  `gitlab trigger` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.project\_id | string | 
action\_result\.parameter\.trigger\_name | string | 
action\_result\.summary\.trigger\_token | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.data | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list triggers'
List the pipeline triggers of a GitLab project

Type: **investigate**  
Read only: **True**

List the triggers of a GitLab project\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**project\_id** |  required  | The ID of the GitLab project | numeric |  `gitlab project id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.project\_id | numeric | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 
action\_result\.data\.\*\.description | string | 
action\_result\.data\.\*\.token | string | 
action\_result\.data\.\*\.id | numeric |   

## action: 'run pipeline'
Execute a pipeline on a particular branch of a project

Type: **generic**  
Read only: **False**

Execute a pipeline on a particular branch of a project\. GitLab CI/CD must be configured on the project for this action to succeed\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**project\_id** |  required  | The ID of the GitLab project | numeric |  `gitlab project id` 
**trigger\_token** |  required  | The trigger token required for executing a pipeline | string |  `gitlab trigger` 
**branch** |  required  | The branch containing the \.gitlab\-ci\.yml file to run\. Defaults to 'master' | string |  `branch name` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.project\_id | numeric | 
action\_result\.parameter\.trigger\_token | string | 
action\_result\.parameter\.branch | string | 
action\_result\.summary\.pipeline\_id | string | 
action\_result\.summary\.pipeline\_web\_url | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.data | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 