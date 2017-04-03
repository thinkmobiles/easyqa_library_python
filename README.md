# EasyQA Python 2 Client Library

This document describes Python 2 library that wraps [EasyQA](https://geteasyqa.com) REST API.

# Installation
```sh
$ pip install easyqa
```
### Authenticating
###### fields
[required]
> - email - Your email
> - password - Your password
> - project_token - Your project token. [How find project token](https://geteasyqa.com/sdk/android)

```python
from easyqa.session import Session
easyqa = Session('email', 'password', 'project_token')
```
# Methods

### Issues
#### Get issue
##### Get issues from project
```python
# get all issues from project
easyqa.get_issues()
```
##### Get issue by id
###### fields
[required]
> - issue_id - Issue ID

```python
# get one issue by id
easyqa.get_issue_by_id(issue_id)

# get one issue by id in project
easyqa.get_issue_by_id_in_project(issue_id)
```

#### Create issue
###### fields
[required]
> - summary - Issue summary

[optional]
> - test_object_id - ID test object on site
> - description - Issue description
> - issue_type - Type of issue
> - priority - Issue priority
> - severity - Issue severity
> - assigner_id - Issue assigner ID
> - test.jpg - Name your upload image. Data type must be "jpg"
> - test.mp4 - Name your upload video. Data type must be "mp4"

```python
# create one issue
easyqa.create_issue(summary, **kwargs)
```

###### examples
```python
# create one issue with optional fields
easyqa.create_issue(summary='Test', description='test description')
```
#### Update issue
###### fields
[required]
> - issue_id - Issue ID
> - summary - Issue summary

[optional]
> - test_object_id - ID test object on site
> - description - Issue description
> - issue_type - Type of issue
> - priority - Issue priority
> - severity - Issue severity
> - assigner_id - Issue assigner ID
> - status_id - Status ID
> - test.jpg - Name your upload image. Data type must be "jpg"
> - test.mp4 - Name your upload video. Data type must be "mp4"

```python
# Update issue by id
easyqa.update_issue_by_id(issue_id, summary, **kwargs)
```

###### examples
```python
# update one issue with optional fields
easyqa.update_issue_by_id(issue_id=2, summary='Test', description='test description')

# update one issue by id in project with optional fields
easyqa.update_issue_by_id_in_project(issue_id=2, summary='Test', description='test description')
```

#### Delete issue
###### fields
[required]
> - issue_id - Issue ID

###### examples
```python
# delete one issue
easyqa.delete_issue_by_id(issue_id=2)

# delete one issue by id in project
easyqa.delete_issue_by_id_in_project(issue_id=3)
```

### Organization
#### Get Organization
##### Get organizations
```python
# get all your organizations
easyqa.get_organizations()
```

##### Get organization by id
###### fields
[required]
> - id - Organization ID

###### examples
```python
# get one organization by id
easyqa.show_organization(id)
```

#### Create organization
###### fields
[required]
> - title - Organization title

[optional]
> - description - Organization description

###### examples
```python
# create one organization 
easyqa.create_organization(title='Test')

# create one organization with optional fields
easyqa.create_issue(title='Test', description='test description')
```

#### Update organization
###### fields
[required]
> - id - Organization id

[optional]
> - title - Organization title
> - description - Organization description

###### examples
```python
# update one organization 
easyqa.update_organization(id=1, title='Test', description='test description')
```

#### Delete organization
###### fields
[required]
> - id - Organization id

###### examples
```python
# delete one organization
easyqa.delete_organization(id=2)
```

### Project
#### Get Project
##### Get all your Projects
```python
# get all your projects
easyqa.get_projects()
```
##### Get project by id
###### fields
[required]
> - id - Projects ID

###### examples
```python
# get one project by id
easyqa.show_project(id)
```

#### Create project
###### fields
[required]
> - org_id - Organization id
> - title - Project title

###### examples
```python
# create one project 
easyqa.create_project(org_id=1, title='Test')
```

#### Update project
###### fields
[required]
> - org_id - Organization id

[optional]
> - title - Project title

###### examples
```python
# update one project 
easyqa.update_project(org_id=1, title='updated project')
```

#### Delete project
###### fields
[required]
> - id - Project id

###### examples
```python
# delete one project
easyqa.delete_project(id=2)
```

### Roles
#### Get Roles
###### fields
[required]
> - organization_id - Organization id

###### examples
```python
# get all roles from organizations
easyqa.get_roles(organization_id=1)
```

##### Get role by id
###### fields
[required]
> - id - Role ID

###### examples
```python
# get one organization by id
easyqa.show_role(id=1)
```

##### Create organization role
###### fields
[required]
> - organization_id - Organization id
> - user_id - User id
> - role - Role (available: 'user', 'admin')

###### examples
```python
# create organization role
easyqa.create_organization_role(organization_id=1, user_id=12, role='user')
```

##### Create project role
###### fields
[required]
> - organization_id - Organization id
> - user_id - User id
> - role - Role (available: 'developer', 'tester', 'viewer', 'project_manager')

###### examples
```python
# create project role
easyqa.create_project_role(organization_id=1, user_id=12, role='tester')
```

##### Update project role
###### fields
[required]
> - id - role id
> - role - Role (available: 'developer', 'tester', 'viewer', 'project_manager')

###### examples
```python
# update project role
easyqa.update_project_role(id=2, role='tester')
```

##### Delete project role
###### fields
[required]
> - id - role id

###### examples
```python
# delete project role
easyqa.delete_role(id=2)
```

### Test cases
#### Get Test cases
###### fields
[required]
> - test_module_id - Test module ID

###### examples
```python
# get all test cases from module
easyqa.get_test_cases(test_module_id=1)
```

##### Get test case by id
###### fields
[required]
> - id - Test case ID

###### examples
```python
# get one test case by id
easyqa.show_test_case(id=1)
```

##### Create test case
###### fields
[required]
> - test_module_id - Test module ID
> - title - Title of the test case

[optional]
> - test_case - Test case attributes
> - pre_steps - Pre steps to test case
> - steps - Steps to test case
> - expected_result - Expected test case result
> - case_type - Type of test case

###### examples
```python
# create test case
easyqa.create_test_case(test_module_id=1, title='test', steps='1. Sit in a Vulture Droid\n 2. Go to Lothal')
```

##### Update test case
###### fields
[required]
> - id - Test case ID
> - title - Title of the test case

[optional]
> - test_case - Test case attributes
> - pre_steps - Pre steps to test case
> - steps - Steps to test case
> - expected_result - Expected test case result
> - case_type - Type of test case

###### examples
```python
# update test case
easyqa.update_test_case(test_module_id=1, title='test', pre_steps='1. Sit in a Vulture Droid\n 2. Go to Lothal')
```

##### Delete test case
###### fields
[required]
> - id - test case id

###### examples
```python
# delete test case
easyqa.delete_test_case(id=2)
```

### Statuses
#### Get Statuses
###### fields

###### examples
```python
# get all statuses
easyqa.get_statuses()
```

##### Get status by id
###### fields
[required]
> - id - Status id

###### examples
```python
# get one status by id
easyqa.show_statuses(id=1)
```

##### Create status
###### fields
[required]
> - name - Status name

###### examples
```python
# create status
easyqa.create_status(name='synthesizing')
```

##### Update status
###### fields
[required]
> - name - Status name
> - id - Status id

###### examples
```python
# update status
easyqa.update_status(id=4, name='synthesizing')
```

##### Delete status
###### fields
[required]
> - id - Status id

###### examples
```python
# delete status
easyqa.delete_status(id=2)
```

### Test Modules
#### Get Test Modules
###### fields
[required]
> - test_plan_id - ID of test plan

###### examples
```python
# get all test module from test plan
easyqa.get_test_modules(test_plan_id=1)
```

##### Get test module by id
###### fields
[required]
> - id - Test module id

###### examples
```python
# get one test module by id
easyqa.show_test_module(id=1)
```

##### Create test module
###### fields
[required]
> - test_plan_id - ID of test plan
> - title - Title of the test module

[optional]
> - description - Description of the test module
> - test_module - Test module attributes
> - parent_id - Id of parent test module (If you give this parameter, this test module will be nested in parent test module)

###### examples
```python
# create test module
easyqa.create_test_module(test_plan_id=1, title='test', description='Super module')
```

##### Update test module
###### fields
[required]
> - id - Test module id
> - title - Title of the test module

[optional]
> - description - Description of the test module
> - test_module - Test module attributes
> - parent_id - Id of parent test module (If you give this parameter, this test module will be nested in parent test module)

###### examples
```python
# update test module
easyqa.update_test_module(test_plan_id=1, title='test', description='Super module2')
```

##### Delete test module
###### fields
[required]
> - id - test module

###### examples
```python
# delete test module
easyqa.delete_test_module(id=2)
```