# Overview

To interact with your Komand system, an API is available.

## Permissions

If you do n ot have the right permissions, the following error message will be posted

````
{"message":"checkpermission: You do not have the right permissions to access this resource","status":"ACCESS_DENIED"}
````

# Login / Authorisation

Login / Authorisation is done with JWT (JSON Web Token).

## URL

```
POST https://komandurl/v2/sessions
```

## Response

## Sampe data

Cannot post that because don't want to disclose my data. But it will look like the following:

```
{"token":"eyJhbG........"}
```

That token string is a base64 encoded json object:

```
{"alg":"HS256","typ":"JWT"}{"enable_licensing":true,"exp":123455,"hashed_account_id":"aaaaaaaaaaaaaaaaaaaaaa","iat":1540453818,"komand_branch":"master","komand_revision":"46547f857dfd862ce7d82d526ce8f94d42b600f5","komand_version":"0.4000","pendo_account":"aaaaaaaaaaa","perms":["PLUGIN_MODIFY","WORKFLOW_MODIFY","CONNECTION_MODIFY","USER_CREATE","USER_MANAGER","APP","PRODUCT_KEY_VIEW"],"sub":"jaegeral","user":{"user_id":1,"user_name":"admin","inactive":false,"first_name":"Admin","last_name":"admin","company_title":"","avatar_url":""}
```

## Sample POST

```
curl -X POST -k -H 'Accept: application/json' -H 'Accept.Encoding: gzip, deflate, br' -i 'https://komandurl/v2/sessions' --data '{"user_name": "admin", "user_secret": "PASSWORD"}'
```

That token can then be used for authentitcate other API endpoints e.g.:

## Sample Authentication

```
curl -X GET -k -H 'Authorization: Bearer <token>' -i 'https://komandurl/v2/connections'
```


# All Jobs

Be careful with that query, as it will output a lot of data!!!

## URL

```
https://komandurl/v2/jobs
```

# Dedicated Job

## URL

```
GET https://komandurl/v2/jobs/$JOB-ID
```

If you are not logged in you might need to use the Authorization header as well (not tested).

## Example Response

```json
{"job_id":"5822ab3e-d784-11e8-9f8b-f2801f1b9fd1","type":"active","workflow_uid":"5822ae2c-d784-11e8-9f8b-f2801f1b9fd1","version_uid":"5822b1ec-d784-11e8-9f8b-f2801f1b9fd1","group_id":"5822b458-d784-11e8-9f8b-f2801f1b9fd1","name":"Test_workflow","status":"failed","created_at":"2018-10-24T11:36:17Z","ended_at":"2018-10-24T11:36:22Z","updated_at":"2018-10-24T11:36:22Z","context":{"data":{"$URL":"http://127.0.0.1:8000/jobs/details/5822ab3e-d784-11e8-9f8b-f2801f1b9fd1","$created_at":"2018-10-24T11:36:17.632193167Z","$id":"5822ab3e-d784-11e8-9f8b-f2801f1b9fd1","$name":"Test_workflow","$start_message":{"Parameter":48284},"Test_workflow":{"$success":true,"asdasd":48284},"Step_1":{"$success":false}},"stack":[{"parent_step_uid":"","parent_step_name":"","loop_index":-1}]},"traversed_paths":[{"path_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","workflow_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","workflow_version_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","from_step_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","to_step_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","name":"","description":"","created_at":"0001-01-01T00:00:00Z","updated_at":"0001-01-01T00:00:00Z"}],"potential_next_paths":[{"path_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","workflow_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","workflow_version_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","from_step_uid":"b501f592-80d4-adb7-911f-e1cb0261a4fa","to_step_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","name":"","description":"","created_at":"0001-01-01T00:00:00Z","updated_at":"0001-01-01T00:00:00Z"}],"next_step_uids":[],"time_spent":4.607579602,"investigation_id":"","viewed_by_id":null,"owned_by_id":null,"failed_step_id":1855707,"failed_step_name":"Step_1","is_rerunnable":true,"errors":null}
```

## Sample request

```
curl -X GET -k -H 'Authorization: Bearer <token>' -i 'https://<komandurl>/v2/jobs/<jobid>'
```

# Triggers

Are used to basically start every workflow from external if you have an API trigger.

## URL

```
https://komandurl/v2/trigger/$WORKFLOWID/events
```

## Example Response

````
{"message":"trigger event published to queue"}
`````

# Connections

Get all connections of a Komand system

````
https://komandurl/v2/connections
````

## Example Response

None

# Users

Get all users of a system

````
https://komandurl/v2/users
````

## Example response

```
{"users":[{"user_id":1,"user_name":"komand","inactive":false,"first_name":"Komand","last_name":"Admin","company_title":"","avatar_url":"https://www.gravatar.com/avatar/277afd6a111494867161f6a67c228726?d=mm","email":"komand@example.com","role_name":"administrator","role":{"name":"administrator","description":"Administrator","permissions":["PLUGIN_MODIFY","WORKFLOW_MODIFY","CONNECTION_MODIFY","USER_CREATE","USER_MANAGER","APP","PRODUCT_KEY_VIEW"]}}}
```

# Plugins

Provides a JSON list of all installed plugins (be careful, lot of data!)

```
https://komandurl/v2/plugins
```

# Post a Job

In addition to the events/trigger it is also possible to post a job and get the Job ID back

## URL

```
https://komandurl/v2/workflows/<workflowid>/events
```

## Example

```
curl -X POST -k -H 'Authorization: Bearer <token>' -i 'https://<komandurl>/v2/workflows/<workflowid>/events' --data '{"key": "value", "job_id": "123123", "text_post": "123123"}'
```

## Sample response

```
{"job_id":"7b345d83-ab70-4b19-b2a0-019718245678","job_url":"http://127.0.0.1:8000/jobs/details/7b345d83-ab70-4b19-b2a0-019718245678","message":"event published to queue"}
```

