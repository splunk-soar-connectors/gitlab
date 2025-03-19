# GitLab

Publisher: Peter Bertel \
Connector Version: 2.0.0 \
Product Vendor: GitLab \
Product Name: GitLab \
Minimum Product Version: 6.0.0

This app integrates with a GitLab instance to perform various lookups and execute CI/CD pipelines

### Configuration variables

This table lists the configuration variables required to operate GitLab. These variables are specified when configuring a GitLab asset in Splunk SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**gitlab_location** | required | string | The Hostname or IP address of the GitLab instance |
**personal_access_token** | required | password | Access token for a GitLab user |

### Supported Actions

[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration \
[list users](#action-list-users) - List all the users in the GitLab instance \
[list projects](#action-list-projects) - List all the projects in the GitLab instance \
[list branches](#action-list-branches) - List the branches of a GitLab project \
[create trigger](#action-create-trigger) - Create a new pipeline trigger for a GitLab project \
[list triggers](#action-list-triggers) - List the pipeline triggers of a GitLab project \
[run pipeline](#action-run-pipeline) - Execute a pipeline on a particular branch of a project

## action: 'test connectivity'

Validate the asset configuration for connectivity using supplied configuration

Type: **test** \
Read only: **True**

#### Action Parameters

No parameters are required for this action

#### Action Output

No Output

## action: 'list users'

List all the users in the GitLab instance

Type: **investigate** \
Read only: **True**

#### Action Parameters

No parameters are required for this action

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.data | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | |
summary.total_objects_successful | numeric | | |
action_result.data.\*.username | string | `user name` | testuser |
action_result.data.\*.can_create_project | boolean | | True False |

## action: 'list projects'

List all the projects in the GitLab instance

Type: **investigate** \
Read only: **True**

#### Action Parameters

No parameters are required for this action

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | |
summary.total_objects_successful | numeric | | |
action_result.data.\*.\*.name | string | | project-name |
action_result.data.\*.\*.path | string | | path-to/project-name |

## action: 'list branches'

List the branches of a GitLab project

Type: **investigate** \
Read only: **True**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**project_id** | required | The ID of the GitLab project | numeric | `gitlab project id` |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.project_id | numeric | `gitlab project id` | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | |
summary.total_objects_successful | numeric | | |
action_result.data.\*.name | string | | master |

## action: 'create trigger'

Create a new pipeline trigger for a GitLab project

Type: **generic** \
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**project_id** | required | The ID of the GitLab project | numeric | `gitlab project id` |
**trigger_name** | required | The name of the new trigger | string | `gitlab trigger` |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.project_id | string | `gitlab project id` | |
action_result.parameter.trigger_name | string | `gitlab trigger` | |
action_result.summary.trigger_token | string | | 100fadfa454da4b3e1d4d3b9243d78 |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.data | string | | |
summary.total_objects | numeric | | |
summary.total_objects_successful | numeric | | |

## action: 'list triggers'

List the pipeline triggers of a GitLab project

Type: **investigate** \
Read only: **True**

List the triggers of a GitLab project.

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**project_id** | required | The ID of the GitLab project | numeric | `gitlab project id` |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.project_id | numeric | `gitlab project id` | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | |
summary.total_objects_successful | numeric | | |
action_result.data.\*.description | string | | Sample trigger description |
action_result.data.\*.token | string | | 123456abcdef |
action_result.data.\*.id | numeric | | 1 |

## action: 'run pipeline'

Execute a pipeline on a particular branch of a project

Type: **generic** \
Read only: **False**

Execute a pipeline on a particular branch of a project. GitLab CI/CD must be configured on the project for this action to succeed.

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**project_id** | required | The ID of the GitLab project | numeric | `gitlab project id` |
**trigger_token** | required | The trigger token required for executing a pipeline | string | `gitlab trigger` |
**branch** | required | The branch containing the .gitlab-ci.yml file to run. Defaults to 'master' | string | `branch name` |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.project_id | numeric | `gitlab project id` | |
action_result.parameter.trigger_token | string | `gitlab trigger` | |
action_result.parameter.branch | string | `branch name` | |
action_result.summary.pipeline_id | string | | 21 |
action_result.summary.pipeline_web_url | string | | https://gitlab.domain.com/test-group/test-project/pipelines/21 |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.data | string | | |
summary.total_objects | numeric | | |
summary.total_objects_successful | numeric | | |

______________________________________________________________________

Auto-generated Splunk SOAR Connector documentation.

Copyright 2025 Splunk Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and limitations under the License.
