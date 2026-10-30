# Endpoints

Generated from the live OpenAPI documents (`openapi/main.json`, `openapi/hub.json`).

## The HTTP_API

Base URL: `https://eval.cultureyes.ae/api/v1`

| Method | Path | Summary |
|---|---|---|
| `POST` | `/api/v1/admin/task-sets` | Import a Task_Set_Definition |
| `POST` | `/api/v1/admin/seasons` | Create a Season draft |
| `PATCH` | `/api/v1/admin/seasons/{season_id}/hub-chat-judge-version` | Set a Season draft's Hub_Chat Judge_Version |
| `PATCH` | `/api/v1/admin/seasons/{season_id}/tracks/{track}/settings` | Set a Season draft's Track settings |
| `POST` | `/api/v1/admin/seasons/{season_id}/start` | Start a Season |
| `POST` | `/api/v1/admin/judge-versions` | Register a Judge_Version |
| `GET` | `/api/v1/admin/configuration` | The current configuration |
| `POST` | `/api/v1/admin/configuration` | Submit a configuration change |
| `GET` | `/api/v1/admin/review-entries` | The open review entries |
| `GET` | `/api/v1/admin/review-entries/{entry_id}` | One review entry |
| `POST` | `/api/v1/admin/review-entries/{entry_id}/regrade` | Re-grade the entry's Grading_Failed Items |
| `POST` | `/api/v1/admin/review-entries/{entry_id}/new-report` | Request one new Report |
| `POST` | `/api/v1/admin/review-entries/{entry_id}/new-sandbox` | Continue the held Load_Check or run with a new Sandbox |
| `POST` | `/api/v1/admin/access-grants` | Issue a read-only AccessGrant |
| `POST` | `/api/v1/admin/hub-chat-grants` | Issue a Hub_Chat conversation AccessGrant |
| `POST` | `/api/v1/admin/runs/{run_id}/technical-notices` | Attach a Technical_Notice |
| `POST` | `/api/v1/admin/runs/{run_id}/defect-notices` | Confirm a defect and attach a Defect_Notice |
| `POST` | `/api/v1/admin/runs/{origin_run_id}/verification-reruns` | Request a verification re-run |
| `POST` | `/api/v1/admin/record-import` | Import an Evaluation_Record for display |
| `GET` | `/api/v1/audit` | The Audit_Log entries visible to the caller |
| `POST` | `/api/v1/auth/sign-in` | Start an OIDC sign-in |
| `GET` | `/api/v1/auth/callback` | OIDC sign-in callback |
| `POST` | `/api/v1/auth/register` | Complete a first sign-in with the registration fields |
| `POST` | `/api/v1/auth/sign-out` | Sign out |
| `GET` | `/api/v1/auth/whoami` | What the current session is |
| `POST` | `/api/v1/runs/{origin_run_id}/defect-reruns` | Request a Defect re-run of an origin Evaluation_Run |
| `GET` | `/api/v1/health` | Liveness check |
| `PUT` | `/api/v1/runs/{run_id}/results` | Immutable Runscores |
| `PATCH` | `/api/v1/runs/{run_id}/results` | Immutable Runscores |
| `DELETE` | `/api/v1/runs/{run_id}/results` | Immutable Runscores |
| `POST` | `/api/v1/runs/{run_id}/results` | Immutable Runscores |
| `GET` | `/api/v1/runs/{run_id}/results` | The Recorded_Result view of an Evaluation_Run |
| `PUT` | `/api/v1/runs/{run_id}/results/{rest}` | Immutable Runscores Item |
| `PATCH` | `/api/v1/runs/{run_id}/results/{rest}` | Immutable Runscores Item |
| `DELETE` | `/api/v1/runs/{run_id}/results/{rest}` | Immutable Runscores Item |
| `POST` | `/api/v1/runs/{run_id}/results/{rest}` | Immutable Runscores Item |
| `PUT` | `/api/v1/runs/{run_id}/items` | Immutable Itemgrade |
| `PATCH` | `/api/v1/runs/{run_id}/items` | Immutable Itemgrade |
| `DELETE` | `/api/v1/runs/{run_id}/items` | Immutable Itemgrade |
| `POST` | `/api/v1/runs/{run_id}/items` | Immutable Itemgrade |
| `GET` | `/api/v1/runs/{run_id}/items` | The paginated Item view of an Evaluation_Run |
| `PUT` | `/api/v1/runs/{run_id}/items/{rest}` | Immutable Itemgrade Item |
| `PATCH` | `/api/v1/runs/{run_id}/items/{rest}` | Immutable Itemgrade Item |
| `DELETE` | `/api/v1/runs/{run_id}/items/{rest}` | Immutable Itemgrade Item |
| `POST` | `/api/v1/runs/{run_id}/items/{rest}` | Immutable Itemgrade Item |
| `PUT` | `/api/v1/runs/{run_id}/report` | Immutable Report |
| `PATCH` | `/api/v1/runs/{run_id}/report` | Immutable Report |
| `DELETE` | `/api/v1/runs/{run_id}/report` | Immutable Report |
| `POST` | `/api/v1/runs/{run_id}/report` | Immutable Report |
| `PUT` | `/api/v1/runs/{run_id}/report/{rest}` | Immutable Report Item |
| `PATCH` | `/api/v1/runs/{run_id}/report/{rest}` | Immutable Report Item |
| `DELETE` | `/api/v1/runs/{run_id}/report/{rest}` | Immutable Report Item |
| `POST` | `/api/v1/runs/{run_id}/report/{rest}` | Immutable Report Item |
| `PUT` | `/api/v1/runs/{run_id}/regrade` | Immutable Itemgrade |
| `PATCH` | `/api/v1/runs/{run_id}/regrade` | Immutable Itemgrade |
| `DELETE` | `/api/v1/runs/{run_id}/regrade` | Immutable Itemgrade |
| `POST` | `/api/v1/runs/{run_id}/regrade` | Immutable Itemgrade |
| `PUT` | `/api/v1/runs/{run_id}/regrade/{rest}` | Immutable Itemgrade Item |
| `PATCH` | `/api/v1/runs/{run_id}/regrade/{rest}` | Immutable Itemgrade Item |
| `DELETE` | `/api/v1/runs/{run_id}/regrade/{rest}` | Immutable Itemgrade Item |
| `POST` | `/api/v1/runs/{run_id}/regrade/{rest}` | Immutable Itemgrade Item |
| `POST` | `/api/v1/internal/uploads/authorize` | The tusd pre-create hook |
| `POST` | `/api/v1/internal/uploads/finished` | The tusd post-finish hook |
| `POST` | `/api/v1/internal/payment-webhook` | The payment provider's webhook |
| `PUT` | `/api/v1/runs/{run_id}/owner-comment` | Save the Owner_Comment of an Evaluation_Run |
| `DELETE` | `/api/v1/runs/{run_id}/owner-comment` | Delete the Owner_Comment of an Evaluation_Run |
| `GET` | `/api/v1/runs/{run_id}/publication` | The publication preview of an Evaluation_Run |
| `POST` | `/api/v1/runs/{run_id}/publication` | Publish an Evaluation_Run |
| `PATCH` | `/api/v1/runs/{run_id}/publication` | Change the Report link answer of a published entry |
| `DELETE` | `/api/v1/runs/{run_id}/publication` | Withdraw a published entry |
| `GET` | `/api/v1/runs/{run_id}/load-check` | The Load_Check outputs of an Evaluation_Run |
| `GET` | `/api/v1/runs/{run_id}/export` | Export the Evaluation_Record of an Evaluation_Run |
| `POST` | `/api/v1/submissions/{submission_id}/runs` | Request a new Evaluation_Run of a Submission |
| `GET` | `/api/v1/runs/{run_id}` | The Run_Status view of an Evaluation_Run |
| `DELETE` | `/api/v1/runs/{run_id}` | Delete an Evaluation_Run's Evaluation_Record |
| `POST` | `/api/v1/runs/{run_id}/continue` | Confirm to continue after a duplicate-fingerprint hold |
| `POST` | `/api/v1/runs/{run_id}/confirm` | Confirm the Load_Check result of an Evaluation_Run |
| `POST` | `/api/v1/runs/{run_id}/cancel` | Cancel an Evaluation_Run |
| `POST` | `/api/v1/submissions` | Create a Submission |
| `POST` | `/api/v1/submissions/{submission_id}/finish-upload` | Mark the upload of a Submission as finished |
| `GET` | `/api/v1/submissions/{submission_id}/declaration-change-set` | The pending Declaration change set |
| `POST` | `/api/v1/submissions/{submission_id}/declaration-versions` | Commit the pending Declaration change set |
| `POST` | `/api/v1/submissions/{submission_id}/link` | Link the Submission to an earlier checkpoint |
| `DELETE` | `/api/v1/submissions/{submission_id}/files` | Request deletion of the Submission's files |
| `GET` | `/api/v1/auth/tokens` | List the Personal_Access_Tokens of the signed-in account |
| `POST` | `/api/v1/auth/tokens` | Create a Personal_Access_Token |
| `DELETE` | `/api/v1/auth/tokens/{token_id}` | Revoke a Personal_Access_Token |

## The Hub (public)

Base URL: `https://eval.cultureyes.ae/public`

| Method | Path | Summary |
|---|---|---|
| `GET` | `/public/hub-chat` | The Hub_Chat's opening notice |
| `POST` | `/public/hub-chat/messages` | Send one Hub_Chat message |
| `GET` | `/public/hub-chat/conversation` | This session's Hub_Chat conversation |
| `GET` | `/public/seasons/{name}/tracks/{track}/download` | Download one Leaderboard table |
| `GET` | `/public/seasons` | The Leaderboard |
| `GET` | `/public/seasons/{name}/tracks/{track}/leaderboard` | One Season-and-Track table |
| `GET` | `/public/seasons/{name}/settings` | One Season's settings page |
| `GET` | `/public/models/{entry_id}` | One public model page |
| `GET` | `/public/documentation` | The HTTP_API documentation page |
