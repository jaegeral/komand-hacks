# Overview

To interact with your Komand system, an API is available.

# Jobs

## URL

```
https://komandurl/v2/jobs/$JOB-ID
```

If you are not logged in you might need to use the Authorization header as well (not tested).

## Example Response

```json
{"job_id":"5822ab3e-d784-11e8-9f8b-f2801f1b9fd1","type":"active","workflow_uid":"5822ae2c-d784-11e8-9f8b-f2801f1b9fd1","version_uid":"5822b1ec-d784-11e8-9f8b-f2801f1b9fd1","group_id":"5822b458-d784-11e8-9f8b-f2801f1b9fd1","name":"Test_workflow","status":"failed","created_at":"2018-10-24T11:36:17Z","ended_at":"2018-10-24T11:36:22Z","updated_at":"2018-10-24T11:36:22Z","context":{"data":{"$URL":"http://127.0.0.1:8000/jobs/details/5822ab3e-d784-11e8-9f8b-f2801f1b9fd1","$created_at":"2018-10-24T11:36:17.632193167Z","$id":"5822ab3e-d784-11e8-9f8b-f2801f1b9fd1","$name":"Test_workflow","$start_message":{"Parameter":48284},"Test_workflow":{"$success":true,"asdasd":48284},"Step_1":{"$success":false}},"stack":[{"parent_step_uid":"","parent_step_name":"","loop_index":-1}]},"traversed_paths":[{"path_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","workflow_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","workflow_version_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","from_step_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","to_step_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","name":"","description":"","created_at":"0001-01-01T00:00:00Z","updated_at":"0001-01-01T00:00:00Z"}],"potential_next_paths":[{"path_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","workflow_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","workflow_version_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","from_step_uid":"b501f592-80d4-adb7-911f-e1cb0261a4fa","to_step_uid":"5822b6a6-d784-11e8-9f8b-f2801f1b9fd1","name":"","description":"","created_at":"0001-01-01T00:00:00Z","updated_at":"0001-01-01T00:00:00Z"}],"next_step_uids":[],"time_spent":4.607579602,"investigation_id":"","viewed_by_id":null,"owned_by_id":null,"failed_step_id":1855707,"failed_step_name":"Step_1","is_rerunnable":true,"errors":null}
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



