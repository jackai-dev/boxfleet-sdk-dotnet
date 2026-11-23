# BoxFleet hosted control plane (boxfleet.io) .NET API

<!-- omniwrap-api-reference eyJjb250cmFjdF9maW5nZXJwcmludCI6ImUzZmQ0Yzc0NGFlODkzM2MwZTBiZDBjMjFhNjkyODk3Nzk1YTE0NjU3ZTU3N2ZiODIxMDg1MDBkMzlmMmFjOGQiLCJvcGVyYXRpb25fY291bnQiOjU2LCJyZW5kZXJlciI6ImRvdG5ldCIsInZlcnNpb24iOiIxLjUuMCJ9 -->

This generated index is tied to Semantic IR `1.14.0` and contract fingerprint `e3fd4c744ae8933c0e0bd0c21a692897795a14657e577fb82108500d39f2ac8d`. Every operation below is rendered from the same semantic contract and artifact-attested public member allocation as the SDK.

SDK maturity: **experimental**  
Artifact evidence: [`omniwrap-artifact.json`](omniwrap-artifact.json) binds this file by SHA-256 and is revalidated by the package gate.

## Client hooks and tracing

`new ClientOptions { Hooks = new RequestHooks { ... } }` registers four callbacks. Every attempt starts with `BeforeRequest` and ends with exactly one of `OnRetry` (another attempt follows), `AfterResponse` (the success the call returns) or `OnError` (the failure the call reports). Each receives the operation id, the HTTP method, the URL, the request headers, the attempt number (from 1), the time elapsed since the call started and, once the server answered, the HTTP status. No context carries a credential: `Authorization`, `Proxy-Authorization`, `Cookie`, every API-key header and API-key query parameter, and any configured credential value read `[redacted]`. Every context is an immutable `HookContext` record: no hook can change the request.

`new ClientOptions { Tracer = ... }` opens one span per call through the tracer interface this SDK defines, named after the operation id, with `http.request.method`, `http.response.status_code` and `http.request.resend_count`. It needs no tracing library; README.md maps it onto the OpenTelemetry API.

## Shared types

- `HostedPersistentBoxClose`
- `HostedPersistentBoxRead`
- `HostedPersistentUsageMeter`
- `HostedPersistentUsageRead`
- `ObservedBox`

## Resource `Accounts`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJBY2NvdW50cy5HZXRDb25maWdBc3luYyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEFjY291bnRzQ29uZmlnIiwicGF0aCI6Ii92MS9hY2NvdW50cy9jb25maWciLCJyZXNvdXJjZSI6IkFjY291bnRzIiwic2VjdGlvbl9zaGEyNTYiOiI2MjUyN2MyODE3MGIyODNjN2I4ZWZiZTY3ZDNmMjgwYzNiN2EyNmY0MGM1ZmE0YTk4YmZkMjA2M2U1Nzc5ODg2Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImNhNDYxOGVlYmMwNmM0M2UyODIwZjc1ZmQxYTMwNzJiOTNlNGJhNTIwMWUyOTZiY2ZkNmNmOThiYjIyN2NiODIifQ -->
### `client.Accounts.GetConfigAsync`

Operation ID: `getAccountsConfig`  
Route: `GET` `/v1/accounts/config`  
Equivalent member: `client.GetAccountsConfigAsync`  

#### Signature

```csharp
public Task GetConfigAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Accounts.GetConfigAsync();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBY2NvdW50c0NvbmZpZyJ9 -->

## Resource `Admin`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJBZG1pbi5Db250cm9sVXNlckFzeW5jIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNvbnRyb2xVc2VyIiwicGF0aCI6Ii92MS9hZG1pbi91c2VycyIsInJlc291cmNlIjoiQWRtaW4iLCJzZWN0aW9uX3NoYTI1NiI6ImUwZGNhYTM2MGQ0YjE3OWRjODE2MjZkZDBhNDEzOWEwNDUyYWIwM2VmMGVhOGE0NjFlM2ZjZTI5Y2YwOWVkOWIiLCJzaWduYXR1cmVfc2hhMjU2IjoiN2NiOWNkYTg2NDI5MjVhMmVjNzBjNDMyNTYxNWFjZWQzYTMwNGQ4OWExNjYwNGE3ZjYyNzBhY2ZhY2JjZTUwNiJ9 -->
### `client.Admin.ControlUserAsync`

Operation ID: `controlUser`  
Route: `POST` `/v1/admin/users`  
Equivalent member: `client.ControlUserAsync`  

#### Signature

```csharp
public Task ControlUserAsync(
IReadOnlyDictionary<string, JsonElement> body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Applied | none |
| `401` | Admin token required | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Admin.ControlUserAsync(body: {});
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjb250cm9sVXNlciJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJBZG1pbi5HZXRDb25zb2xlQXN5bmMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRBZG1pbkNvbnNvbGUiLCJwYXRoIjoiL3YxL2FkbWluL2NvbnNvbGUiLCJyZXNvdXJjZSI6IkFkbWluIiwic2VjdGlvbl9zaGEyNTYiOiJjMTcwNWI5YzBkZWFkNjI2Yzk5ZmM1YmQxY2ZiZTNiYTkyMWNmYWU1NTU4N2MwZWFiMDU0MTI4Y2EyMzllMTQ5Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjFjODVhOTVjNGRjOWFjOGYwNGE3M2ZlZTgyZmRkOWM0NzRkN2FiYjg4ODg4MGI4OTFlODgzOTdkZDFkN2UzYjEifQ -->
### `client.Admin.GetConsoleAsync`

Operation ID: `getAdminConsole`  
Route: `GET` `/v1/admin/console`  
Equivalent member: `client.GetAdminConsoleAsync`  

#### Signature

```csharp
public Task GetConsoleAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Console | none |
| `401` | Admin token required | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Admin.GetConsoleAsync();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBZG1pbkNvbnNvbGUifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJBZG1pbi5HZXRQbGFuc0FzeW5jIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0QWRtaW5QbGFucyIsInBhdGgiOiIvdjEvYWRtaW4vcGxhbnMiLCJyZXNvdXJjZSI6IkFkbWluIiwic2VjdGlvbl9zaGEyNTYiOiJjYzM2MGYwN2JiNDkyMDE5ODdjZTUyMTc1MTZlZDk0ODMzYzI4YzYzZjNkYTUzODdkMGYxNDBlMzM3ZGQ4NTNkIiwic2lnbmF0dXJlX3NoYTI1NiI6IjJmZTA1ZTBhMTdjZGI1MDZlZjQyMzVkNzU2NTQzNDFhM2RkNmMwMzdmMTE5NjIzMWYxOGZkY2YwYmRjNjliZjYifQ -->
### `client.Admin.GetPlansAsync`

Operation ID: `getAdminPlans`  
Route: `GET` `/v1/admin/plans`  
Equivalent member: `client.GetAdminPlansAsync`  

#### Signature

```csharp
public Task GetPlansAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Plans | none |
| `401` | Admin token required | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Admin.GetPlansAsync();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBZG1pblBsYW5zIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJBZG1pbi5MaXN0VXNlcnNBc3luYyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RVc2VycyIsInBhdGgiOiIvdjEvYWRtaW4vdXNlcnMiLCJyZXNvdXJjZSI6IkFkbWluIiwic2VjdGlvbl9zaGEyNTYiOiJkMzgyZmZlYjljNDIyYTNiNmNkYjRmZTBlYTY0NDQwNWY4NWZiYjA3NDg5ZDRhYTEzNDVlYmZiZGYyNmQ4MDFiIiwic2lnbmF0dXJlX3NoYTI1NiI6IjI5YWZmMmQ2YmU4YmE0NGY3ZTFkYTg4ZGY1ODAzZWFhODQwZDY2NzNiNzQyZjk5MGQzYjIzNmE5ZTVjMTk4MDgifQ -->
### `client.Admin.ListUsersAsync`

Operation ID: `listUsers`  
Route: `GET` `/v1/admin/users`  
Equivalent member: `client.ListUsersAsync`  

#### Signature

```csharp
public Task ListUsersAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Users | none |
| `401` | Admin token required | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Admin.ListUsersAsync();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0VXNlcnMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJBZG1pbi5SZWFkVGVsZW1ldHJ5QXN5bmMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJyZWFkVGVsZW1ldHJ5IiwicGF0aCI6Ii92MS9hZG1pbi90ZWxlbWV0cnkiLCJyZXNvdXJjZSI6IkFkbWluIiwic2VjdGlvbl9zaGEyNTYiOiIyYThkYmE0ZjE4MzU3NTA4OGJiYzVlZWUzN2E1YTM2NjNjNWMwNmM3YTk4ZDhiNTMzZDg3NTJhMzgxZTJkMDY1Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjUyMGIwNmVlODU1NDY4YjMxM2RhMzJmOTg1ZDM1NzAwOTc2ZmIwMWEzZDE4NDkxYjNkMWU5YWQ3NTY5YWU0MzMifQ -->
### `client.Admin.ReadTelemetryAsync`

Operation ID: `readTelemetry`  
Route: `GET` `/v1/admin/telemetry`  
Equivalent member: `client.ReadTelemetryAsync`  

#### Signature

```csharp
public Task ReadTelemetryAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Events | none |
| `401` | Admin token required | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Admin.ReadTelemetryAsync();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWFkVGVsZW1ldHJ5In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJBZG1pbi5VcGRhdGVQbGFuQXN5bmMiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoidXBkYXRlUGxhbiIsInBhdGgiOiIvdjEvYWRtaW4vcGxhbnMiLCJyZXNvdXJjZSI6IkFkbWluIiwic2VjdGlvbl9zaGEyNTYiOiIzNzZmNTgzZGJlNGJlNGZlZjBjMWJiOWE0ZjNjNjdlMzgxYzYzYjhjMzUzZWVkYTlmNjJmNGEzZDc5ODRjZjkxIiwic2lnbmF0dXJlX3NoYTI1NiI6Ijg5OTA3MDg3OTNmZGUwNTczNzQ0MWQyNzM0ZDA4ZDllZTQ4NDNkNGQ0Y2Y5NmMxODMyODM1OGFkMzk4ODk4YWEifQ -->
### `client.Admin.UpdatePlanAsync`

Operation ID: `updatePlan`  
Route: `POST` `/v1/admin/plans`  
Equivalent member: `client.UpdatePlanAsync`  

#### Signature

```csharp
public Task UpdatePlanAsync(
IReadOnlyDictionary<string, JsonElement> body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Updated | none |
| `401` | Admin token required | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Admin.UpdatePlanAsync(body: {});
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJ1cGRhdGVQbGFuIn0 -->

## Resource `Auth`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJBdXRoLkdldEdhdGVBc3luYyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEF1dGhHYXRlIiwicGF0aCI6Ii92MS9hdXRoL2dhdGUiLCJyZXNvdXJjZSI6IkF1dGgiLCJzZWN0aW9uX3NoYTI1NiI6IjI1MGI3NmM4ZDNjYzJlNjc4NTZhMmViZWYwMjdjMTRhMWE3ZjJiNWM1NzI0MWJiN2E0ZmQ4MWUwNGZkYTMzNzMiLCJzaWduYXR1cmVfc2hhMjU2IjoiZjI4NzQyZTg0ZWUzZjJiM2I4ZmRjYzI2NmVmMWU3YzE4ZmFmMWJjZTY1NDU3MjlhNTllY2YzNmVhZjlmYjEyZiJ9 -->
### `client.Auth.GetGateAsync`

Operation ID: `getAuthGate`  
Route: `GET` `/v1/auth/gate`  
Equivalent member: `client.GetAuthGateAsync`  

#### Signature

```csharp
public Task GetGateAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Auth.GetGateAsync();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBdXRoR2F0ZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJBdXRoLlJlZ2lzdGVyQXN5bmMiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicmVnaXN0ZXIiLCJwYXRoIjoiL3YxL2F1dGgvcmVnaXN0ZXIiLCJyZXNvdXJjZSI6IkF1dGgiLCJzZWN0aW9uX3NoYTI1NiI6IjljNGU4MmJkZGQ1NzExYjZmYmJiOTQ0ZmVhODgxMjY1ZTU1MzZmN2U4YzNlNjIwMjRhZWI5ZGYwMDAzZTA3MjkiLCJzaWduYXR1cmVfc2hhMjU2IjoiOWRjM2YxMmI5MGFjMDFjNmMzNzU3ZjhjNzNjNjUzNGFiNmQ1NzI0ZTk2YjViNDFiNDYxOGE2OWM0NTFiYTBlYSJ9 -->
### `client.Auth.RegisterAsync`

Operation ID: `register`  
Route: `POST` `/v1/auth/register`  
Equivalent member: `client.RegisterAsync`  

#### Signature

```csharp
public Task RegisterAsync(
IReadOnlyDictionary<string, JsonElement> body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | License issued | none |
| `202` | Verification code sent (or withheld by the resend cooldown) | none |
| `400` | Invalid or expired code | none |
| `403` | Not invited or refused | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |
| `429` | Rate limited | none |
| `503` | Registration not configured | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Auth.RegisterAsync(body: {});
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWdpc3RlciJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJBdXRoLlVwZGF0ZUdhdGVBc3luYyIsIm1ldGhvZCI6IlBVVCIsIm9wZXJhdGlvbl9pZCI6InVwZGF0ZUF1dGhHYXRlIiwicGF0aCI6Ii92MS9hdXRoL2dhdGUiLCJyZXNvdXJjZSI6IkF1dGgiLCJzZWN0aW9uX3NoYTI1NiI6IjkzYWQwMmYzOTQ3NTg1MTAyOWIxODU3NzM3NDdjMzhkYzliY2Y2NDAzMGRjNjZkOTE3YWEwNzUzZGJjNDlmMmQiLCJzaWduYXR1cmVfc2hhMjU2IjoiZDA3ZDg1MzkxNDIyNGQwYjQ0NjgyMDU1OTQ0ODE3MjQxZGNlZWQzYTFmMTZkZmJhMDk1MDQ0OTYxZTYyYTBmMSJ9 -->
### `client.Auth.UpdateGateAsync`

Operation ID: `updateAuthGate`  
Route: `PUT` `/v1/auth/gate`  
Equivalent member: `client.UpdateAuthGateAsync`  

#### Signature

```csharp
public Task UpdateGateAsync(
IReadOnlyDictionary<string, JsonElement> body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Updated | none |
| `401` | Admin token required | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Auth.UpdateGateAsync(body: {});
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJ1cGRhdGVBdXRoR2F0ZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJBdXRoLlZlcmlmeUxpY2Vuc2VBc3luYyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJ2ZXJpZnlMaWNlbnNlIiwicGF0aCI6Ii92MS9hdXRoL3ZlcmlmeSIsInJlc291cmNlIjoiQXV0aCIsInNlY3Rpb25fc2hhMjU2IjoiMDczMjhlZWI5MWE2YWIzMjBhM2QzODc3YTdkODYwZDU2MmZlMmU0N2JkNTBmY2ZkZjZhYWRiY2NmYzg4NzkxZiIsInNpZ25hdHVyZV9zaGEyNTYiOiI0ZmI1OTlhOWVkMDgwODNjOWUxMWE4YzYxZjA1YjlkNGQ3OTFiNzk0YzJiODA3MTFjNjM3NWJlNDcxZDY5MzRjIn0 -->
### `client.Auth.VerifyLicenseAsync`

Operation ID: `verifyLicense`  
Route: `POST` `/v1/auth/verify`  
Equivalent member: `client.VerifyLicenseAsync`  

#### Signature

```csharp
public Task VerifyLicenseAsync(
IReadOnlyDictionary<string, JsonElement> body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Valid | none |
| `401` | Invalid license | none |
| `403` | Refused | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |
| `503` | Verification not configured | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Auth.VerifyLicenseAsync(body: {});
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJ2ZXJpZnlMaWNlbnNlIn0 -->

## Resource `Billing`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJCaWxsaW5nLlN0cmlwZVdlYmhvb2tBc3luYyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJzdHJpcGVXZWJob29rIiwicGF0aCI6Ii92MS9iaWxsaW5nL3N0cmlwZS93ZWJob29rIiwicmVzb3VyY2UiOiJCaWxsaW5nIiwic2VjdGlvbl9zaGEyNTYiOiIwMzdjNGFkOGVlZTEzZmEwM2Q0NGY2OGU0YzVmMmQ4NTNkYmI2ZTU1NzVhMDM3M2VkZGM3Zjg3MTY3MWY3ZmM1Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjZlZmI4MjkzMDRjMWYwYjFhY2Q0MTYwMDM4NWQ2YzdiOGU1NzQzYTE5NjY0ZTRlMjY4OThmYThiZDRhM2ZlMzAifQ -->
### `client.Billing.StripeWebhookAsync`

Operation ID: `stripeWebhook`  
Route: `POST` `/v1/billing/stripe/webhook`  
Equivalent member: `client.StripeWebhookAsync`  

#### Signature

```csharp
public Task StripeWebhookAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Received | none |
| `400` | Invalid signature or payload | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Billing.StripeWebhookAsync();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdHJpcGVXZWJob29rIn0 -->

## Resource `Health`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJIZWFsdGguR2V0QXN5bmMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRIZWFsdGgiLCJwYXRoIjoiL2hlYWx0aCIsInJlc291cmNlIjoiSGVhbHRoIiwic2VjdGlvbl9zaGEyNTYiOiJiMjc0ZDJiNTE2ZTI3ZTkyMTMxNTdiZDUyZTRkMzY3ZDE0OGEwZWQzMmZlODIyMjk3ODY2MzJhZjM0MzdkMzdkIiwic2lnbmF0dXJlX3NoYTI1NiI6IjZkOGViZTBkYjI1NGY1ZTA1NDYxNmY2YzIyOTgwNzYxMDczZWRiZjhjZWE2N2YzZTliM2MxZmE4NzU5NjQ1MjkifQ -->
### `client.Health.GetAsync`

Operation ID: `getHealth`  
Route: `GET` `/health`  
Equivalent member: `client.GetHealthAsync`  

#### Signature

```csharp
public Task GetAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Health.GetAsync();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIZWFsdGgifQ -->

## Resource `Jobs`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJKb2JzLkNhbmNlbEFzeW5jIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNhbmNlbEpvYiIsInBhdGgiOiIvdjEvam9icy97am9iSWR9L2NhbmNlbCIsInJlc291cmNlIjoiSm9icyIsInNlY3Rpb25fc2hhMjU2IjoiNTM0ZDA2YWZkMTZlMTk1NjFkYjgzOGY2N2Y3ZmE1MDkzOTM3NDA5OGNjOWM5ZjQzOWExMzUyYzJlZDMwNjI4MiIsInNpZ25hdHVyZV9zaGEyNTYiOiJkNDM0ZTYyMzNmYWMxMmNkZjMzNWRjNGVmMWVmOTQ5NWU1NDJjZjA1MGE3MDI2ZjJhNjc4OTY5MGM5NTcwNTgxIn0 -->
### `client.Jobs.CancelAsync`

Operation ID: `cancelJob`  
Route: `POST` `/v1/jobs/{jobId}/cancel`  
Equivalent member: `client.CancelJobAsync`  

#### Signature

```csharp
public Task CancelAsync(
string jobId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `jobId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "jobId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Jobs.CancelAsync(jobId: "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjYW5jZWxKb2IifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJKb2JzLkdldEFzeW5jIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0Sm9iIiwicGF0aCI6Ii92MS9qb2JzL3tqb2JJZH0iLCJyZXNvdXJjZSI6IkpvYnMiLCJzZWN0aW9uX3NoYTI1NiI6Ijk1OWFlZmEwNjU4NDlhYzY5MzQ1M2FlNTFhNDNkZDBhZWQ0ODk4YjkwMmE0Mzk3MjA5MDU5MDBmYzZiOGVmMzIiLCJzaWduYXR1cmVfc2hhMjU2IjoiMmJkMmZiOTVlMGIyNWEwZTE1Y2JmMzE2MzI3OTI5NGE0ZDEwZTE4ZTc0ZTIwNmM0MmJkOWNjOGJjYmMzMWFiZSJ9 -->
### `client.Jobs.GetAsync`

Operation ID: `getJob`  
Route: `GET` `/v1/jobs/{jobId}`  
Equivalent member: `client.GetJobAsync`  

#### Signature

```csharp
public Task GetAsync(
string jobId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `jobId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "jobId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Jobs.GetAsync(jobId: "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRKb2IifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJKb2JzLkxpc3RFdmVudHNBc3luYyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RKb2JFdmVudHMiLCJwYXRoIjoiL3YxL2pvYnMve2pvYklkfS9ldmVudHMiLCJyZXNvdXJjZSI6IkpvYnMiLCJzZWN0aW9uX3NoYTI1NiI6IjllZDYxZGE1M2Y4MWI2Mjg4OWE5ZmQxZWMwMzFkMTc5NWIzMTZiMDc2MjhkN2Q4NTY3OThlMzY2ZDA0YjVhMDMiLCJzaWduYXR1cmVfc2hhMjU2IjoiNWZhODc1NDhhZWI1NjIzMmFlYTM0YzM2NTgzMjkzOGY3ZDdhZWExOTNlODk4MDhhMDc5N2IwYjlmYTVjMWNlNyJ9 -->
### `client.Jobs.ListEventsAsync`

Operation ID: `listJobEvents`  
Route: `GET` `/v1/jobs/{jobId}/events`  
Equivalent member: `client.ListJobEventsAsync`  

#### Signature

```csharp
public Task ListEventsAsync(
string jobId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `jobId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "jobId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Jobs.ListEventsAsync(jobId: "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Sm9iRXZlbnRzIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJKb2JzLkxpc3RBc3luYyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RKb2JzIiwicGF0aCI6Ii92MS9qb2JzIiwicmVzb3VyY2UiOiJKb2JzIiwic2VjdGlvbl9zaGEyNTYiOiI5MWJjN2Y4NzI5MjgyNTU2NmM0YjNhMGMyZWExNjM2OTA1YzgxYzEwMTE4NzJiNzc0NzA5YWMyNTlmYTdiZDA4Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjVhZDdhMTU3Njk4OGQ1NWUxZjRhM2NlYThmZTYzZTUxYjE3ZDRmMjJiZjgwOTFiNjYxZDJiY2IwMTcxNWQzOTYifQ -->
### `client.Jobs.ListAsync`

Operation ID: `listJobs`  
Route: `GET` `/v1/jobs`  
Equivalent member: `client.ListJobsAsync`  

#### Signature

```csharp
public Task ListAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Jobs | none |
| `401` | Session required | none |
| `503` | Storage not configured | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Jobs.ListAsync();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Sm9icyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJKb2JzLlN1Ym1pdEFzeW5jIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InN1Ym1pdEpvYiIsInBhdGgiOiIvdjEvam9icyIsInJlc291cmNlIjoiSm9icyIsInNlY3Rpb25fc2hhMjU2IjoiYzdlMzA4NDFkYTgwMzU3YjAyMzM2NjJjNjcxZTRkNjNlMzUyNzZiMDM4NTI1NzFkYTQyYTYyNmE5ZjRkNmYzNSIsInNpZ25hdHVyZV9zaGEyNTYiOiJjYmFkYzRhZDI1ZDY5OGVmM2QxNWQ3MTkwM2E0ZWMzYjUwOGUwYTNhOTFiYmRiNzUwNTIyMjcwMDE4Nzc0ZjEyIn0 -->
### `client.Jobs.SubmitAsync`

Operation ID: `submitJob`  
Route: `POST` `/v1/jobs`  
Equivalent member: `client.SubmitJobAsync`  

#### Signature

```csharp
public Task SubmitAsync(
IReadOnlyDictionary<string, JsonElement> body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Replayed | none |
| `201` | Created | none |
| `401` | Session required | none |
| `503` | Storage not configured | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Jobs.SubmitAsync(body: {});
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdWJtaXRKb2IifQ -->

## Resource `Organizations`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkNsb3NlUGVyc2lzdGVudEJveEFzeW5jIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNsb3NlUGVyc2lzdGVudEJveCIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L3BlcnNpc3RlbnQtYm94ZXMve2JveElkfS9jbG9zZSIsInJlc291cmNlIjoiT3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiYTg5MjFhN2JlZTE1MWRjZjY1N2ZhM2YzMTZiOTNiNjUxODE1OGIzNWQ1YWNjZDI1NWU4YTJlMTJmYzc1YmNiNSIsInNpZ25hdHVyZV9zaGEyNTYiOiIwZWI2NmZkZmQ1ZTE5OTRhYTdjM2FkNmJkZWY3OTg4ZDNkNTliOTk5MjEzMjFhY2U4ZTU4NDZiZmQzYmUzZTdlIn0 -->
### `client.Organizations.ClosePersistentBoxAsync`

Operation ID: `closePersistentBox`  
Route: `POST` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}/close`  
Equivalent member: `client.ClosePersistentBoxAsync`  

#### Signature

```csharp
public Task<HostedPersistentBoxClose> ClosePersistentBoxAsync(
string organizationId,
Guid boxId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Closure is recorded; repeat requests return the same result without deleting again. | application/json (HostedPersistentBoxClose) |
| `202` | Closure is unconfirmed. Lost, late, negative or mismatched acknowledgements and failed receipt persistence retain reservations. Repeat requests never dispatch another deletion; operator reconciliation is required. | application/json (HostedPersistentBoxClose) |
| `400` | Invalid UUID, body or query parameters. | none |
| `401` | Missing or rejected product session. | none |
| `403` | Current authority denied cleanup or the organization/product/environment differs. | none |
| `404` | No durable box in this exact target scope. | none |
| `409` | Unconfirmed or changed provider allocation requires operator reconciliation. | none |
| `503` | Authority or storage unavailable, or no matching operator provider adapter. Missing configuration refuses before any close intention or deletion. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-c54d-988d0e4e7e77"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.ClosePersistentBoxAsync(organizationId: "example", boxId: "00000000-0000-0000-c54d-988d0e4e7e77");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjbG9zZVBlcnNpc3RlbnRCb3gifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkNyZWF0ZUJpbGxpbmdQb3J0YWxBc3luYyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjcmVhdGVCaWxsaW5nUG9ydGFsIiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vYmlsbGluZy9wb3J0YWwiLCJyZXNvdXJjZSI6Ik9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6ImYyYTE4NzIwZjE2M2VjYTkxNjIxNGQ4YjdiZWYwOTJiZWEzODMyMDcyNzVjZWMwMTEwYzAzODlmOTQ2M2Y0OTciLCJzaWduYXR1cmVfc2hhMjU2IjoiODkwYTVlYjQ3NTIzODZmZDgzNWE4ZDI2MDAzZmM0MjBiNzMzZmY0MTU2OTVjN2MxMTZiNWEzZWZiOWRkYjUyYSJ9 -->
### `client.Organizations.CreateBillingPortalAsync`

Operation ID: `createBillingPortal`  
Route: `POST` `/v1/organizations/{organizationId}/billing/portal`  
Equivalent member: `client.CreateBillingPortalAsync`  

#### Signature

```csharp
public Task CreateBillingPortalAsync(
string organizationId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | portalUrl | none |
| `404` | No Stripe customer yet | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.CreateBillingPortalAsync(organizationId: "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVCaWxsaW5nUG9ydGFsIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkNyZWF0ZUJveEFzeW5jIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNyZWF0ZUJveCIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L2JveGVzIiwicmVzb3VyY2UiOiJPcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiI0MTI0ZjllNTJkNmUwYWU1MzFiYmUwZTE3ZjViM2MyYTkxZTdlM2FkNzc1MGEwYjMwNTNkYzgzNzgwZDAzYzlhIiwic2lnbmF0dXJlX3NoYTI1NiI6ImE5YWY1YjcxZTJkNTk5MDk5NmFmOGYxNmE2M2MwNGU5YWEyNjcxMmYyOGI2MmZkOGMxZjAyNzViYjM2YTBlNzYifQ -->
### `client.Organizations.CreateBoxAsync`

Operation ID: `createBox`  
Route: `POST` `/v1/organizations/{organizationId}/boxes`  
Equivalent member: `client.CreateBoxAsync`  

#### Signature

```csharp
public Task CreateBoxAsync(
string organizationId,
CreateBoxRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Box running at the provider | none |
| `402` | Concurrent-box limit reached | none |
| `502` | The provider refused; recorded as failed | none |
| `503` | No provider or no storage | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.CreateBoxAsync(organizationId: "example", body: {});
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVCb3gifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkNyZWF0ZUNoZWNrb3V0QXN5bmMiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY3JlYXRlQ2hlY2tvdXQiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9iaWxsaW5nL2NoZWNrb3V0IiwicmVzb3VyY2UiOiJPcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiJmZWEzMGFkNjEwYzc3ZGJjZmQzYmMxNjI1MjE2YzE4NTk4MjdhMDhmODJjMzMxODczNzgwMjU5MDk2NDk2MzdkIiwic2lnbmF0dXJlX3NoYTI1NiI6IjQzZTNmN2UxMzBmNzM2NTMzNjE1NzU4YTE0YTgwNDlhMTBkMmRkODBhNGY1Njk0Y2MwNTQ1YTk5YjAyYmVhODEifQ -->
### `client.Organizations.CreateCheckoutAsync`

Operation ID: `createCheckout`  
Route: `POST` `/v1/organizations/{organizationId}/billing/checkout`  
Equivalent member: `client.CreateCheckoutAsync`  

#### Signature

```csharp
public Task CreateCheckoutAsync(
string organizationId,
CreateCheckoutRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | checkoutUrl of the Stripe Checkout Session | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. Autonomous mode: Plan not on sale or subscription exists | none |

#### Canonical required-input example

```json
{
  "body": {
    "planKey": "pro"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.CreateCheckoutAsync(organizationId: "example", body: {"planKey": "pro"});
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVDaGVja291dCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkdldEJpbGxpbmdBc3luYyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEJpbGxpbmciLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9iaWxsaW5nIiwicmVzb3VyY2UiOiJPcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiJmMDBlY2MzOWM3OWZhNTFiZmFkMTAyNTZhNmNkOWJjMTI4Yjk2ZWFlMWFiOGMxZDhiZjRiZGQxYTc5NTIwNzNiIiwic2lnbmF0dXJlX3NoYTI1NiI6IjRmOWI5MTZmY2ViMTY3ODE3MWJjNmJiYThkMTc4NDQyYzY5YTNmMjcyNTRkODExNjhkYjZlZTYyZTk2NDAyMjcifQ -->
### `client.Organizations.GetBillingAsync`

Operation ID: `getBilling`  
Route: `GET` `/v1/organizations/{organizationId}/billing`  
Equivalent member: `client.GetBillingAsync`  

#### Signature

```csharp
public Task GetBillingAsync(
string organizationId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Billing status | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.GetBillingAsync(organizationId: "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRCaWxsaW5nIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkdldEJveEFzeW5jIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0Qm94IiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vYm94ZXMve2JveElkfSIsInJlc291cmNlIjoiT3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiOGUyMTUxMWNjZTNkZTgyOTM5YTlhY2UwZjEwMTJjOWY4OTUyNzkyYWViNzBlODRiNGNlMzBkNTRlMTBhNjY5NSIsInNpZ25hdHVyZV9zaGEyNTYiOiJkNzM1ZThmYjhjMGY1NDIxNzI1ZWJhZDQ2ZjRhNWY2ZjQ1N2Y0OTRmMDg5ZWM0YmM5ZTQ2MzBmMDUwNDFkOWIwIn0 -->
### `client.Organizations.GetBoxAsync`

Operation ID: `getBox`  
Route: `GET` `/v1/organizations/{organizationId}/boxes/{boxId}`  
Equivalent member: `client.GetBoxAsync`  

#### Signature

```csharp
public Task GetBoxAsync(
string organizationId,
Guid boxId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stored box | none |
| `404` | Unknown box | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-d32a-0e84cb70d88a"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.GetBoxAsync(organizationId: "example", boxId: "00000000-0000-0000-d32a-0e84cb70d88a");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRCb3gifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkdldEVudGl0bGVtZW50c0FzeW5jIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0RW50aXRsZW1lbnRzIiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vZW50aXRsZW1lbnRzIiwicmVzb3VyY2UiOiJPcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiJmNGJmMTdhMzZhMmNlZTZhMjEzOTUzZmIwNjA1MTM5ZWUyZDFkM2EwNWY4MzlkNzI1NzBjYzNlNzUwNDY0MDgxIiwic2lnbmF0dXJlX3NoYTI1NiI6IjYyOWU4YWViOWZiOTRiMGI3YjA0ZTE4Nzc0N2ZmZjBlMmY1Njk1YWMyN2ZlZWRmNjA3ZTY5OWE5MzFlZmE3NmMifQ -->
### `client.Organizations.GetEntitlementsAsync`

Operation ID: `getEntitlements`  
Route: `GET` `/v1/organizations/{organizationId}/entitlements`  
Equivalent member: `client.GetEntitlementsAsync`  

#### Signature

```csharp
public Task GetEntitlementsAsync(
string organizationId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Entitlements and usage | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.GetEntitlementsAsync(organizationId: "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRFbnRpdGxlbWVudHMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkdldEZsZWV0QXN5bmMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRGbGVldCIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L2ZsZWV0IiwicmVzb3VyY2UiOiJPcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiIwODY5OTBiZTRlZmY2MWM1ZGFkYzdlMDdjY2Q3ZDM5YjdmZWIwNTk2NzY3OTdlZWJlOTlmODk0YWFlZWQ5YTQ2Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImQ0YjVlMmVkOWY3Y2IxY2RkZWM5M2FmYTM1YTExOWViZDZmZGQ1Mjk1ZjUyYzAxNGU4MGRmYTQ5NzNhZGFiNzYifQ -->
### `client.Organizations.GetFleetAsync`

Operation ID: `getFleet`  
Route: `GET` `/v1/organizations/{organizationId}/fleet`  
Equivalent member: `client.GetFleetAsync`  

#### Signature

```csharp
public Task GetFleetAsync(
string organizationId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stored fleet | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.GetFleetAsync(organizationId: "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRGbGVldCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkdldEZsZWV0UG9saWN5QXN5bmMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRGbGVldFBvbGljeSIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L2ZsZWV0L3BvbGljeSIsInJlc291cmNlIjoiT3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiYTQyYzczNmMwZTg2YjViYTg2MGY1OTU1OWE5OWQ1MTc1NTRkYjI4MWI3ODQxNmYzOGMwZGM0MDkwNmQyZmI0MyIsInNpZ25hdHVyZV9zaGEyNTYiOiJjZDFmOWY3ZTQyOWI0NTA2NTI0ZWY5MzkxNWI3YzBjNjE3MzFjMjljMDA5MWQ2ODMxYjE1ODRhYmFjOWY5YzlmIn0 -->
### `client.Organizations.GetFleetPolicyAsync`

Operation ID: `getFleetPolicy`  
Route: `GET` `/v1/organizations/{organizationId}/fleet/policy`  
Equivalent member: `client.GetFleetPolicyAsync`  

#### Signature

```csharp
public Task GetFleetPolicyAsync(
string organizationId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Effective policy | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.GetFleetPolicyAsync(organizationId: "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRGbGVldFBvbGljeSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkdldFBlcnNpc3RlbnRCb3hBc3luYyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldFBlcnNpc3RlbnRCb3giLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9wZXJzaXN0ZW50LWJveGVzL3tib3hJZH0iLCJyZXNvdXJjZSI6Ik9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6IjQ3YzYwM2VmZDY2ZTNiMDZiZWE1YmVlYWVhYWJjZTA5YmI0M2I1ZmViYmZiZGJkYzliYjhlZmMxOWIwOGMzMTkiLCJzaWduYXR1cmVfc2hhMjU2IjoiNmJkMzc4ZWQ0NzhlYzk0ZjRlY2RlOWIxMTgzNTQ4NDBmNmM4MjAwMDdkMmE1NWJjNzI3NjRmYjE4MmYzZWY3MiJ9 -->
### `client.Organizations.GetPersistentBoxAsync`

Operation ID: `getPersistentBox`  
Route: `GET` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}`  
Equivalent member: `client.GetPersistentBoxAsync`  

#### Signature

```csharp
public Task<JsonElement> GetPersistentBoxAsync(
string organizationId,
Guid boxId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Private stored record and reserved budget; runtime status is not-metered. | application/json (object) |
| `400` | Invalid UUID or query parameters. | none |
| `401` | Missing or rejected product session. | none |
| `403` | Current authority denied access or the organization/product/environment differs. | none |
| `404` | No durable box in this exact target scope. | none |
| `503` | Authority or durable record storage unavailable. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-098c-d4f2b24057fb"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.GetPersistentBoxAsync(organizationId: "example", boxId: "00000000-0000-0000-098c-d4f2b24057fb");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRQZXJzaXN0ZW50Qm94In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkdldFBlcnNpc3RlbnRCb3hQcm92aWRlclVzYWdlQXN5bmMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRQZXJzaXN0ZW50Qm94UHJvdmlkZXJVc2FnZSIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L3BlcnNpc3RlbnQtYm94ZXMve2JveElkfS91c2FnZSIsInJlc291cmNlIjoiT3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiODIyZDQyNTgwYTM4MmE5MGViNmIzMGZkYjMwZjE0MzU2ODM2ZTNkNDYyYTM1MzczZTViNzE1NmQ4MzU0NzY3MyIsInNpZ25hdHVyZV9zaGEyNTYiOiI4NWYzODExMTJiM2VjOTJiZmMwODY4NGY5MjE5ZjBjNTJjMmFiNGY0MThkYzIxYWY4NzE3NTk2NzU4OTlmMTlkIn0 -->
### `client.Organizations.GetPersistentBoxProviderUsageAsync`

Operation ID: `getPersistentBoxProviderUsage`  
Route: `GET` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}/usage`  
Equivalent member: `client.GetPersistentBoxProviderUsageAsync`  

#### Signature

```csharp
public Task<JsonElement> GetPersistentBoxProviderUsageAsync(
string organizationId,
Guid boxId,
DateTimeOffset _from,
DateTimeOffset to,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `from` | `query` | yes | `string&lt;date-time&gt;` |  |
| `to` | `query` | yes | `string&lt;date-time&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Private provider evidence summary with explicit interval coverage. | application/json (object) |
| `400` | Invalid box ID or bounded UTC window. | none |
| `401` | Missing or rejected product session. | none |
| `403` | Current authority denied access or target scope differs. | none |
| `404` | No durable box in this exact target scope. | none |
| `413` | Stored evidence exceeds the per-read record bound; select a smaller window. | none |
| `503` | Authority or usage storage unavailable. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-0848-7a89fcbe4ab4"
    },
    {
      "in": "query",
      "name": "from",
      "value": "2026-01-01T00:00:00Z"
    },
    {
      "in": "query",
      "name": "to",
      "value": "2026-01-01T00:00:27Z"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.GetPersistentBoxProviderUsageAsync(organizationId: "example", boxId: "00000000-0000-0000-0848-7a89fcbe4ab4", from: "2026-01-01T00:00:00Z", to: "2026-01-01T00:00:27Z");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRQZXJzaXN0ZW50Qm94UHJvdmlkZXJVc2FnZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkxpc3RCb3hlc0FzeW5jIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdEJveGVzIiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vYm94ZXMiLCJyZXNvdXJjZSI6Ik9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6IjFmODVmMzU2ZmMyZjg3MWM3YmRiOWNmNTY2ZGI5ZTVmYjg4NTZmOWFhNzE0ZDU3YjI4NjUxNDRiNjg0NjlmZTciLCJzaWduYXR1cmVfc2hhMjU2IjoiYzYxMWFmNDU3NmRjNDFkY2Y2Y2QyNDNlNzQ4NzNjMmQ2NWM4MzhkOTQ0MWUzMzhlMjA5YTZlNTA2MDQyMWFkOSJ9 -->
### `client.Organizations.ListBoxesAsync`

Operation ID: `listBoxes`  
Route: `GET` `/v1/organizations/{organizationId}/boxes`  
Equivalent member: `client.ListBoxesAsync`  

#### Signature

```csharp
public Task ListBoxesAsync(
string organizationId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stored boxes with their provider state | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.ListBoxesAsync(organizationId: "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Qm94ZXMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkxpc3RJbnZvaWNlc0FzeW5jIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdEludm9pY2VzIiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vYmlsbGluZy9pbnZvaWNlcyIsInJlc291cmNlIjoiT3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiZDhmMjM0MmZiZWRlYmJmNzgwMTIxMWNiNjUyZTIyY2Q1ZDQ5YjU4ZTVmNmE3MjE1YjgwMzIyNWJhMzU0NGFlZSIsInNpZ25hdHVyZV9zaGEyNTYiOiI3MDgxNDM0YzUzYzgzMzY1MmIxNGU5N2ZiOGMzOWZlMjk4ZTRmZTk3YTM0ZDg2YjVhYzA0Y2YyNGNiMWRlNGExIn0 -->
### `client.Organizations.ListInvoicesAsync`

Operation ID: `listInvoices`  
Route: `GET` `/v1/organizations/{organizationId}/billing/invoices`  
Equivalent member: `client.ListInvoicesAsync`  

#### Signature

```csharp
public Task ListInvoicesAsync(
string organizationId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Invoices | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.ListInvoicesAsync(organizationId: "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0SW52b2ljZXMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkxpc3RNZW1iZXJzQXN5bmMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0TWVtYmVycyIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L21lbWJlcnMiLCJyZXNvdXJjZSI6Ik9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6IjU1YjdlYjliYzliMzM3MTUzYzM0YWYwMTA0MGVlMTBkNjZlYzRlYmViYTU4NDc2YmE5OWRjNGJhNjk3OTkwYjIiLCJzaWduYXR1cmVfc2hhMjU2IjoiYTUxOGExZWY0YzllMDkxM2FiMDkxZTMzY2UwYTkzYjM4ZTBjNzg3ZTc1Y2EwM2Q1ZWNkMzk5OTQ1OTBiNGYzOSJ9 -->
### `client.Organizations.ListMembersAsync`

Operation ID: `listMembers`  
Route: `GET` `/v1/organizations/{organizationId}/members`  
Equivalent member: `client.ListMembersAsync`  

#### Signature

```csharp
public Task ListMembersAsync(
string organizationId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stored members and the plan seat limit | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.ListMembersAsync(organizationId: "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0TWVtYmVycyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkxpc3RPYnNlcnZlZEJveGVzQXN5bmMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0T2JzZXJ2ZWRCb3hlcyIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L29ic2VydmVkLWJveGVzIiwicmVzb3VyY2UiOiJPcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiJjZGE2NTg2NGJlMGYwNmIwODhkYmU2MjEwOWQwNTMwZjQ3Y2U3MmUzZmQ3N2EwMzg1OTBkZWM1MTkzNjA2YmNkIiwic2lnbmF0dXJlX3NoYTI1NiI6Ijk0MjFmYmJlY2NmZWI2MmIzZmFiNzVmYmMxNjExMmQxOGE2NTMyODY4M2FkODNlY2U3Y2I4MWU4NzUzMDIyMDYifQ -->
### `client.Organizations.ListObservedBoxesAsync`

Operation ID: `listObservedBoxes`  
Route: `GET` `/v1/organizations/{organizationId}/observed-boxes`  
Equivalent member: `client.ListObservedBoxesAsync`  

#### Signature

```csharp
public Task<JsonElement> ListObservedBoxesAsync(
string organizationId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Up to 100 non-expired client snapshots, private and not cacheable. | application/json (object) |
| `401` | No valid product session. | none |
| `403` | Organization or scope denied. | none |
| `503` | Inventory storage unavailable. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.ListObservedBoxesAsync(organizationId: "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0T2JzZXJ2ZWRCb3hlcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkxpc3RQZXJzaXN0ZW50Qm94T2ZmZXJzQXN5bmMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0UGVyc2lzdGVudEJveE9mZmVycyIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L3BlcnNpc3RlbnQtYm94ZXMvb2ZmZXJzIiwicmVzb3VyY2UiOiJPcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiJhOWJjM2EyZGUwZDE2MDAxMDM2MjlkZGUzNWRlYzI3ZjUzMjU1NmU0NDk4OWE0NGJlNzE5M2Q0MmVhZTI4NTYyIiwic2lnbmF0dXJlX3NoYTI1NiI6ImZkNzY3NDcwMmJhYzlkNjM2ZjA4ZTg5YTRmZDkzZDQ1NTNiNGU5MjMyYTgwYjEwNTQ1NGU3NjViMWVkZDMwODQifQ -->
### `client.Organizations.ListPersistentBoxOffersAsync`

Operation ID: `listPersistentBoxOffers`  
Route: `GET` `/v1/organizations/{organizationId}/persistent-boxes/offers`  
Equivalent member: `client.ListPersistentBoxOffersAsync`  

#### Signature

```csharp
public Task<JsonElement> ListPersistentBoxOffersAsync(
string organizationId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Private configured offers. | application/json (object) |
| `401` | Product session required. | none |
| `403` | Current read authority denied. | none |
| `503` | Storage or operator offer configuration unavailable. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.ListPersistentBoxOffersAsync(organizationId: "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0UGVyc2lzdGVudEJveE9mZmVycyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLkxpc3RQZXJzaXN0ZW50Qm94ZXNBc3luYyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RQZXJzaXN0ZW50Qm94ZXMiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9wZXJzaXN0ZW50LWJveGVzIiwicmVzb3VyY2UiOiJPcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiJmMzI5MGI3MDJhMDFlNWE1YzMwZTJiYTI1OWEzMTNhNDc5YjM5MjRiY2VkNzc0YWE4YzE5MmU2MjJlNDIzNzlhIiwic2lnbmF0dXJlX3NoYTI1NiI6IjE1ZTNlZmFmZTM3M2FmODMzODBmYTc0Mjc5ZjRhZjc1MjcxM2YxYWY3NjUyMjRmMTJjZDg0ZTM4NzliZTljMWIifQ -->
### `client.Organizations.ListPersistentBoxesAsync`

Operation ID: `listPersistentBoxes`  
Route: `GET` `/v1/organizations/{organizationId}/persistent-boxes`  
Equivalent member: `client.ListPersistentBoxesAsync`  

#### Signature

```csharp
public Task<JsonElement> ListPersistentBoxesAsync(
string organizationId,
long? limit = null,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `limit` | `query` | no | `integer` | Maximum recent records; duplicates and other query parameters are rejected. |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Bounded stored records, private and not cacheable. limitReached indicates the requested bound was filled, not an exact total or proof that more records exist. | application/json (object) |
| `400` | Invalid query parameters. | none |
| `401` | Missing or rejected product session. | none |
| `403` | Current authority denied access or the organization/product/environment differs. | none |
| `503` | Authority or durable record storage unavailable. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.ListPersistentBoxesAsync(organizationId: "example", /* optional: limit */);
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0UGVyc2lzdGVudEJveGVzIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLlByb3Zpc2lvblBlcnNpc3RlbnRCb3hBc3luYyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJwcm92aXNpb25QZXJzaXN0ZW50Qm94IiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vcGVyc2lzdGVudC1ib3hlcyIsInJlc291cmNlIjoiT3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiM2E1MjM5MDk3YmJiZDhiODRkYWQwNDNlNTBiOWViMzgzYTM4M2U1OTY4ZTEzMTU2ODExZTZiNTk1YTE2MmYxYyIsInNpZ25hdHVyZV9zaGEyNTYiOiI5YThmYmIzNjE1MWYyYjYxNzhkNDIzNzZkZDFhOWIzMGUzYzA5YjYyMjM5OWExYjYwYjAzZDQwYTlkNDYzOGIxIn0 -->
### `client.Organizations.ProvisionPersistentBoxAsync`

Operation ID: `provisionPersistentBox`  
Route: `POST` `/v1/organizations/{organizationId}/persistent-boxes`  
Equivalent member: `client.ProvisionPersistentBoxAsync`  

#### Signature

```csharp
public Task ProvisionPersistentBoxAsync(
string organizationId,
ProvisionPersistentBoxRequest body,
string? idempotencyKey = null,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `Idempotency-Key` | `header` | no | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Previously recorded running or closed allocation; replayed is true. | none |
| `201` | Provider allocation confirmed and recorded as running. Runtime remains reserved, not measured. | application/json (object) |
| `202` | The reservation is held and the allocation remains unconfirmed. Repeated requests never dispatch create again; operator reconciliation is required. | none |
| `400` | Invalid body, unsupported fields, query parameters or idempotency key. | none |
| `401` | Missing or rejected product session. | none |
| `402` | Missing durable entitlement, bounded allowance or available capacity. | none |
| `403` | Current authority denied the operation or target scope. | none |
| `409` | Idempotency conflict, unresolved prior budget or UTC month boundary. | none |
| `413` | Request body exceeds 4 KiB. | none |
| `503` | Authority, storage, operator offer or independent runtime enforcement unavailable. Missing configuration is refused before reservation. | none |

#### Canonical required-input example

```json
{
  "body": {
    "offer": "example",
    "reserveMinutes": 1
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.ProvisionPersistentBoxAsync(organizationId: "example", body: {"offer": "example", "reserveMinutes": 1}, /* optional: Idempotency-Key */);
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwcm92aXNpb25QZXJzaXN0ZW50Qm94In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLlB1dEZsZWV0UG9saWN5QXN5bmMiLCJtZXRob2QiOiJQVVQiLCJvcGVyYXRpb25faWQiOiJwdXRGbGVldFBvbGljeSIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L2ZsZWV0L3BvbGljeSIsInJlc291cmNlIjoiT3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiNDkxZTQxNmMxNGUxNjRiY2JkMzExYjFiZjk5YzMwZTAzMjJlMzJmOGYyOTNiN2E4OTQ3OGNhNjk4ZTEwMmE4NiIsInNpZ25hdHVyZV9zaGEyNTYiOiJiNzc2YTk4NDBhMTAyOTE5OTg2YmNmZTM0NmMzNDE2MzRlMWY4NWNkYzk4YWVkNGM3NzFjZmQzYWI1ZTdmNjc2In0 -->
### `client.Organizations.PutFleetPolicyAsync`

Operation ID: `putFleetPolicy`  
Route: `PUT` `/v1/organizations/{organizationId}/fleet/policy`  
Equivalent member: `client.PutFleetPolicyAsync`  

#### Signature

```csharp
public Task PutFleetPolicyAsync(
string organizationId,
PutFleetPolicyRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stored policy | none |
| `400` | Invalid or unenforced field | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.PutFleetPolicyAsync(organizationId: "example", body: {});
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwdXRGbGVldFBvbGljeSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLlJlY29uY2lsZVBlcnNpc3RlbnRCb3hBc3luYyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJyZWNvbmNpbGVQZXJzaXN0ZW50Qm94IiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vcGVyc2lzdGVudC1ib3hlcy97Ym94SWR9L3JlY29uY2lsZSIsInJlc291cmNlIjoiT3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiNjI1MzUyMjk1NTYyOWMyMTZjOTQwMzA2ZTI5NDEzMzczM2YxNWYzZmIyYjA1ZTc2NWZmZmU0NzhmZjg3MzcyNyIsInNpZ25hdHVyZV9zaGEyNTYiOiJlMWZmZjA5MTM1NzVjMTBhYjM0MmUzNjdkMmE0ZTRmYWFiMDE1OTRlNmZhN2YzNjRiM2Q2MDZmYWViMmVhYjkzIn0 -->
### `client.Organizations.ReconcilePersistentBoxAsync`

Operation ID: `reconcilePersistentBox`  
Route: `POST` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}/reconcile`  
Equivalent member: `client.ReconcilePersistentBoxAsync`  

#### Signature

```csharp
public Task<JsonElement> ReconcilePersistentBoxAsync(
string organizationId,
Guid boxId,
ReconcilePersistentBoxRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Confirmed operation or replayed receipt. | application/json (object) |
| `202` | Operation remains unconfirmed; reconcile its operation ID without repeating the mutation. | application/json (object) |
| `400` | Invalid bounded lifecycle request. | none |
| `401` | Product session required. | none |
| `402` | Durable feature or quota denied. | none |
| `403` | Fresh operation authority denied. | none |
| `404` | Box or operation missing in the exact organization and deployment. | none |
| `409` | Conflicting operation, unresolved evidence or unavailable runtime budget. | none |
| `503` | Authority, storage or matching operator adapter unavailable. | none |

#### Canonical required-input example

```json
{
  "body": {
    "operationId": "00000000-0000-0000-f735-3d332872b96e"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-a264-3ce9cdfbbeff"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.ReconcilePersistentBoxAsync(organizationId: "example", boxId: "00000000-0000-0000-a264-3ce9cdfbbeff", body: {"operationId": "00000000-0000-0000-f735-3d332872b96e"});
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWNvbmNpbGVQZXJzaXN0ZW50Qm94In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLlJlbW92ZU1lbWJlckFzeW5jIiwibWV0aG9kIjoiREVMRVRFIiwib3BlcmF0aW9uX2lkIjoicmVtb3ZlTWVtYmVyIiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vbWVtYmVycy97dXNlcklkfSIsInJlc291cmNlIjoiT3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiZjkzNWRmZTAzM2NiNTY1NWI1YjBiMjMzOWMxY2NlOWYyYzNlYzUxYTNhZWU1NDkxZjY1ZmZiZjMyNTMwMDNkNyIsInNpZ25hdHVyZV9zaGEyNTYiOiJlNTNmNWVmZjBmYWRkYmEyMGJlZWJiOGFkNTg4Y2JmZTRlOWZjZTM1OTY4MDk4ZTRiZDljNzZiOGNhZWZmM2E3In0 -->
### `client.Organizations.RemoveMemberAsync`

Operation ID: `removeMember`  
Route: `DELETE` `/v1/organizations/{organizationId}/members/{userId}`  
Equivalent member: `client.RemoveMemberAsync`  

#### Signature

```csharp
public Task RemoveMemberAsync(
string organizationId,
string userId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `userId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Removed | none |
| `404` | Unknown member | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "userId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.RemoveMemberAsync(organizationId: "example", userId: "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZW1vdmVNZW1iZXIifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLlN0YXJ0UGVyc2lzdGVudEJveEFzeW5jIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InN0YXJ0UGVyc2lzdGVudEJveCIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L3BlcnNpc3RlbnQtYm94ZXMve2JveElkfS9zdGFydCIsInJlc291cmNlIjoiT3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiZGEwN2JiYzkzNzk4NzE4ZWZkZWUzYzMzODczMDkwYWU5M2JmNDc5NzU1NjNmYWU2MDEzN2JkMTczZWYyZmJlOSIsInNpZ25hdHVyZV9zaGEyNTYiOiIyODgxOGQ2NDllYjRiZmVmYjEzYTllNTZkNTY3NTIyOThhZjhmOGM1ODY4M2M4ZTA2MTljNTE0MTE5ZGEwNTJlIn0 -->
### `client.Organizations.StartPersistentBoxAsync`

Operation ID: `startPersistentBox`  
Route: `POST` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}/start`  
Equivalent member: `client.StartPersistentBoxAsync`  

#### Signature

```csharp
public Task<JsonElement> StartPersistentBoxAsync(
string organizationId,
Guid boxId,
StartPersistentBoxRequest body,
string? idempotencyKey = null,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `Idempotency-Key` | `header` | no | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Confirmed operation or replayed receipt. | application/json (object) |
| `202` | Operation remains unconfirmed; reconcile its operation ID without repeating the mutation. | application/json (object) |
| `400` | Invalid bounded lifecycle request. | none |
| `401` | Product session required. | none |
| `402` | Durable feature or quota denied. | none |
| `403` | Fresh operation authority denied. | none |
| `404` | Box or operation missing in the exact organization and deployment. | none |
| `409` | Conflicting operation, unresolved evidence or unavailable runtime budget. | none |
| `503` | Authority, storage or matching operator adapter unavailable. | none |

#### Canonical required-input example

```json
{
  "body": {
    "reserveMinutes": 1
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-d7e8-d81c5e30ed9a"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.StartPersistentBoxAsync(organizationId: "example", boxId: "00000000-0000-0000-d7e8-d81c5e30ed9a", body: {"reserveMinutes": 1}, /* optional: Idempotency-Key */);
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdGFydFBlcnNpc3RlbnRCb3gifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLlN0b3BCb3hBc3luYyIsIm1ldGhvZCI6IkRFTEVURSIsIm9wZXJhdGlvbl9pZCI6InN0b3BCb3giLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9ib3hlcy97Ym94SWR9IiwicmVzb3VyY2UiOiJPcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiI1NzYxMWM0MjU2OTM2ZWMyMGYwYzlkNWVhZmQwZWViNTUzOTM0OTBkMDBmMjk3ZDZjNzVlNTZjODhmYzRjZWU4Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjYwZGZhZWE3MDVmNTI0MDg4OWI2YmYyZjkzNjIyOGRkYjVlYTAyMmRmNTIzOTQ3Zjg5Y2FlOWZhZmM3ZGI2YjQifQ -->
### `client.Organizations.StopBoxAsync`

Operation ID: `stopBox`  
Route: `DELETE` `/v1/organizations/{organizationId}/boxes/{boxId}`  
Equivalent member: `client.StopBoxAsync`  

#### Signature

```csharp
public Task StopBoxAsync(
string organizationId,
Guid boxId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stopped | none |
| `502` | The provider refused; state unchanged | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-265e-7c895c60153e"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.StopBoxAsync(organizationId: "example", boxId: "00000000-0000-0000-265e-7c895c60153e");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdG9wQm94In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLlN0b3BQZXJzaXN0ZW50Qm94QXN5bmMiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoic3RvcFBlcnNpc3RlbnRCb3giLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9wZXJzaXN0ZW50LWJveGVzL3tib3hJZH0vc3RvcCIsInJlc291cmNlIjoiT3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiMTE4OTQ1NjkwNGZjYzA4ZTgyNzY0MmQ2M2M2ZTkzYmQyZWVjNjE5ZjdmMDUyZjYzZDRiY2Y3YWUxNzAxNDNmNCIsInNpZ25hdHVyZV9zaGEyNTYiOiI1YTk3OGFmYmFjYmFjNDU3NzBjYjViMTQ5ZmY3OTJmN2QxMmI0ZjUxZjhlMjQ2YmRkMDMyNmNlYTJlYjA1NzdlIn0 -->
### `client.Organizations.StopPersistentBoxAsync`

Operation ID: `stopPersistentBox`  
Route: `POST` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}/stop`  
Equivalent member: `client.StopPersistentBoxAsync`  

#### Signature

```csharp
public Task<JsonElement> StopPersistentBoxAsync(
string organizationId,
Guid boxId,
StopPersistentBoxRequest body,
string? idempotencyKey = null,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `Idempotency-Key` | `header` | no | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Confirmed operation or replayed receipt. | application/json (object) |
| `202` | Operation remains unconfirmed; reconcile its operation ID without repeating the mutation. | application/json (object) |
| `400` | Invalid bounded lifecycle request. | none |
| `401` | Product session required. | none |
| `402` | Durable feature or quota denied. | none |
| `403` | Fresh operation authority denied. | none |
| `404` | Box or operation missing in the exact organization and deployment. | none |
| `409` | Conflicting operation, unresolved evidence or unavailable runtime budget. | none |
| `503` | Authority, storage or matching operator adapter unavailable. | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-978f-a93165cf6579"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.StopPersistentBoxAsync(organizationId: "example", boxId: "00000000-0000-0000-978f-a93165cf6579", body: {}, /* optional: Idempotency-Key */);
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdG9wUGVyc2lzdGVudEJveCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLlN5bmNPYnNlcnZlZEJveGVzQXN5bmMiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoic3luY09ic2VydmVkQm94ZXMiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9vYnNlcnZlZC1ib3hlcy9zeW5jIiwicmVzb3VyY2UiOiJPcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiI4NjQ3NzNjZGVjMWY2MjRjNmM4N2IwOTljODMyZDc4ZDg5Zjk1MDhmZjYyZDc4YTg0MjgzZmUyYTliYTU1OGI2Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjQ0MWUzMGVkM2MwZGZlZTk5YTJhMDUxNjFhMDc2OTdiOWM1MmQwYzFmMmM3ODliNWY4N2Q5OTAyZTQ0ZDMyOWMifQ -->
### `client.Organizations.SyncObservedBoxesAsync`

Operation ID: `syncObservedBoxes`  
Route: `POST` `/v1/organizations/{organizationId}/observed-boxes/sync`  
Equivalent member: `client.SyncObservedBoxesAsync`  

#### Signature

```csharp
public Task<JsonElement> SyncObservedBoxesAsync(
string organizationId,
SyncObservedBoxesRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Snapshot accepted; private and not cacheable. | application/json (object) |
| `400` | Invalid observation snapshot. | none |
| `401` | No valid product session. | none |
| `403` | Organization or scope denied. | none |
| `413` | Snapshot exceeds 64 KiB. | none |
| `503` | Inventory storage unavailable. | none |

#### Canonical required-input example

```json
{
  "body": {
    "boxes": [
      {
        "boxId": "example",
        "kind": "provider-list",
        "provider": "example",
        "state": "running"
      }
    ],
    "sourceId": "00000000-0000-0000-ae61-93cfab8e5e4b"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.SyncObservedBoxesAsync(organizationId: "example", body: {"boxes": [{"boxId": "example", "kind": "provider-list", "provider": "example", "state": "running"}], "sourceId": "00000000-0000-0000-ae61-93cfab8e5e4b"});
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzeW5jT2JzZXJ2ZWRCb3hlcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJPcmdhbml6YXRpb25zLlVwc2VydE1lbWJlckFzeW5jIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InVwc2VydE1lbWJlciIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L21lbWJlcnMiLCJyZXNvdXJjZSI6Ik9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6ImY0MTYxMDMxNWRhMGFiMzdjZDFjNGQ2ZmQ0NmUzM2JmODM1NGI1MWMwODU4ZTViNzYzMzFkNGU3M2U5OTZkN2UiLCJzaWduYXR1cmVfc2hhMjU2IjoiZGNlODhhYzMxNTcyNzBmMWJjNjdkMjRkY2FiMjQ5ZDIwZDI3NDY3NzNmYzBkOGFjYTUxZDZmM2Q1MzA2ODUyZSJ9 -->
### `client.Organizations.UpsertMemberAsync`

Operation ID: `upsertMember`  
Route: `POST` `/v1/organizations/{organizationId}/members`  
Equivalent member: `client.UpsertMemberAsync`  

#### Signature

```csharp
public Task UpsertMemberAsync(
string organizationId,
UpsertMemberRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Member updated | none |
| `201` | Member added | none |
| `402` | Seat limit reached or entitlement missing | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "body": {
    "email": "example-f35c@example.test",
    "role": "owner"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Organizations.UpsertMemberAsync(organizationId: "example", body: {"email": "example-f35c@example.test", "role": "owner"});
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJ1cHNlcnRNZW1iZXIifQ -->

## Resource `Plans`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJQbGFucy5HZXRBc3luYyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldFBsYW5zIiwicGF0aCI6Ii92MS9wbGFucyIsInJlc291cmNlIjoiUGxhbnMiLCJzZWN0aW9uX3NoYTI1NiI6IjJkNjQ4ODAwYjliN2QxNzAyYjY4ODFiZTQzZDFmNDhiNDM3YjNmYmM4N2IwOTJiZjA4NmY3YTA0NzVjZjc0NjMiLCJzaWduYXR1cmVfc2hhMjU2IjoiNmQ4ZWJlMGRiMjU0ZjVlMDU0NjE2ZjZjMjI5ODA3NjEwNzNlZGJmOGNlYTY3ZjNlOWIzYzFmYTg3NTk2NDUyOSJ9 -->
### `client.Plans.GetAsync`

Operation ID: `getPlans`  
Route: `GET` `/v1/plans`  
Equivalent member: `client.GetPlansAsync`  

#### Signature

```csharp
public Task GetAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Plans.GetAsync();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRQbGFucyJ9 -->

## Resource `Telemetry`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJUZWxlbWV0cnkuSW5nZXN0QXN5bmMiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiaW5nZXN0VGVsZW1ldHJ5IiwicGF0aCI6Ii92MS90ZWxlbWV0cnkvaW5nZXN0IiwicmVzb3VyY2UiOiJUZWxlbWV0cnkiLCJzZWN0aW9uX3NoYTI1NiI6IjZlZmQxODljMWZhMGFkOGQ2ZDIyZTU2NWI3Nzk4ZDI5YmY0NmM4ZWUzMjZiNjcyNmUxOTViYTc1NTEyNWEyYTEiLCJzaWduYXR1cmVfc2hhMjU2IjoiNjMwMjNjNjE0OTYxOGIwNzJlNTAxOWVjYzMwYWJiMmIzYmFjYmE1MGVhZjA1ZjdmMWUzYTI5NGExZTc0ZTA5ZSJ9 -->
### `client.Telemetry.IngestAsync`

Operation ID: `ingestTelemetry`  
Route: `POST` `/v1/telemetry/ingest`  
Equivalent member: `client.IngestTelemetryAsync`  

#### Signature

```csharp
public Task IngestAsync(
IReadOnlyDictionary<string, JsonElement> body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Stored | none |
| `400` | Invalid event | none |
| `401` | License required | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |
| `413` | Body too large | none |
| `503` | Ingestion not configured | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Telemetry.IngestAsync(body: {});
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJpbmdlc3RUZWxlbWV0cnkifQ -->

## Resource `Waitlist`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJXYWl0bGlzdC5MaXN0QXN5bmMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0V2FpdGxpc3QiLCJwYXRoIjoiL3YxL3dhaXRsaXN0IiwicmVzb3VyY2UiOiJXYWl0bGlzdCIsInNlY3Rpb25fc2hhMjU2IjoiNDZmNmExNzNiMDdmNzA2NWJhNmZhYTk5ZjVkMDk2YzNhN2Y2ZmM5YmFjNDg3NjQ0ZjBjNDViMGNlYWMzMjUxMiIsInNpZ25hdHVyZV9zaGEyNTYiOiI1YWQ3YTE1NzY5ODhkNTVlMWY0YTNjZWE4ZmU2M2U1MWIxN2Q0ZjIyYmY4MDkxYjY2MWQyYmNiMDE3MTVkMzk2In0 -->
### `client.Waitlist.ListAsync`

Operation ID: `listWaitlist`  
Route: `GET` `/v1/waitlist`  
Equivalent member: `client.ListWaitlistAsync`  

#### Signature

```csharp
public Task ListAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Requests | none |
| `401` | Admin token required | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Waitlist.ListAsync();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0V2FpdGxpc3QifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJXYWl0bGlzdC5SZXF1ZXN0QWNjZXNzQXN5bmMiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicmVxdWVzdEFjY2VzcyIsInBhdGgiOiIvdjEvd2FpdGxpc3QiLCJyZXNvdXJjZSI6IldhaXRsaXN0Iiwic2VjdGlvbl9zaGEyNTYiOiIxNDFlYjllOTg5YjFkNjBiMGViNzJjMTcwNjA0MjM4ODZiM2M5MDJjZjk0OGFkOTcxZDFiNTdkMzc1MjY5NDgwIiwic2lnbmF0dXJlX3NoYTI1NiI6IjVjOWM1YWMyYWNiMWI4MzI3NTUxOTcyYTczMzVjZDlhZmI5ZWRiZjc4NjJmZGNjYTZmMzQ2ZDEwZjc0ZTE2ZGEifQ -->
### `client.Waitlist.RequestAccessAsync`

Operation ID: `requestAccess`  
Route: `POST` `/v1/waitlist`  
Equivalent member: `client.RequestAccessAsync`  

#### Signature

```csharp
public Task RequestAccessAsync(
IReadOnlyDictionary<string, JsonElement> body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `202` | Received | none |
| `400` | Invalid email | none |
| `413` | Body too large | none |
| `429` | Rate limited | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Waitlist.RequestAccessAsync(body: {});
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZXF1ZXN0QWNjZXNzIn0 -->

## Resource `Workspaces`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJXb3Jrc3BhY2VzLkNsb3NlSG9zdGVkQXN5bmMiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY2xvc2VIb3N0ZWRXb3Jrc3BhY2UiLCJwYXRoIjoiL3YxL3dvcmtzcGFjZXMve3dvcmtzcGFjZUlkfS9jbG9zZSIsInJlc291cmNlIjoiV29ya3NwYWNlcyIsInNlY3Rpb25fc2hhMjU2IjoiYWMwY2JmMjZmMjMzY2RhYTFkMDlmOTdhZTc2YzY3ODU5NjkyMTQyY2YzODFhNGUwN2E1OTkyYTJmOGQ0NzUzMiIsInNpZ25hdHVyZV9zaGEyNTYiOiJjNDVlYjNiM2QyZTgyZWRmMTMwMzFjMGRjMDVhMjUwOTUzZGNiOGZmODliZmY2NzFmOTAwNDhmNmNmM2MzODQ0In0 -->
### `client.Workspaces.CloseHostedAsync`

Operation ID: `closeHostedWorkspace`  
Route: `POST` `/v1/workspaces/{workspaceId}/close`  
Equivalent member: `client.CloseHostedWorkspaceAsync`  

#### Signature

```csharp
public Task CloseHostedAsync(
Guid workspaceId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-6658-e129a559a4dd"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Workspaces.CloseHostedAsync(workspaceId: "00000000-0000-0000-6658-e129a559a4dd");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjbG9zZUhvc3RlZFdvcmtzcGFjZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJXb3Jrc3BhY2VzLkdldEhvc3RlZEFzeW5jIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0SG9zdGVkV29ya3NwYWNlIiwicGF0aCI6Ii92MS93b3Jrc3BhY2VzL3t3b3Jrc3BhY2VJZH0iLCJyZXNvdXJjZSI6IldvcmtzcGFjZXMiLCJzZWN0aW9uX3NoYTI1NiI6IjcxNmJlMWJhZDkxZjc5NTdiM2M1Zjc5NjQ0NWVkY2IxZmI5MDdhNjYwNTYwY2MwNTJiN2JhNWMzOTllN2NmNzUiLCJzaWduYXR1cmVfc2hhMjU2IjoiNTcyNDFhYjljNDk0ZWM3NTc2MjUyNzlkMTgxMTcwYTdkNjE3NTUxZTYzYmZjYWMyYTNkOTlhY2QxNjhjOGY2NSJ9 -->
### `client.Workspaces.GetHostedAsync`

Operation ID: `getHostedWorkspace`  
Route: `GET` `/v1/workspaces/{workspaceId}`  
Equivalent member: `client.GetHostedWorkspaceAsync`  

#### Signature

```csharp
public Task GetHostedAsync(
Guid workspaceId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-dd2f-cd2edd1eeb24"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Workspaces.GetHostedAsync(workspaceId: "00000000-0000-0000-dd2f-cd2edd1eeb24");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIb3N0ZWRXb3Jrc3BhY2UifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJXb3Jrc3BhY2VzLkdldEhvc3RlZE9wZXJhdGlvbkFzeW5jIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0SG9zdGVkV29ya3NwYWNlT3BlcmF0aW9uIiwicGF0aCI6Ii92MS93b3Jrc3BhY2VzL3t3b3Jrc3BhY2VJZH0vb3BlcmF0aW9ucy97b3BlcmF0aW9uSWR9IiwicmVzb3VyY2UiOiJXb3Jrc3BhY2VzIiwic2VjdGlvbl9zaGEyNTYiOiJjNTA3ZGNiYzlkZDNjZWNmYzBiOTliNzBmMzViODU5OWNlZTljZDVkZTUzMmE1NjU1Y2RiNzdhOTcwNWZhYjkzIiwic2lnbmF0dXJlX3NoYTI1NiI6IjdiMmIxOGU5ZjRlZjUyNGMyMTQ2OGFiYWIxMjJkYjE2YTc3NmE0NDlkZWJhOWU0MjMzY2M1OWZkZWUzOTJmNjkifQ -->
### `client.Workspaces.GetHostedOperationAsync`

Operation ID: `getHostedWorkspaceOperation`  
Route: `GET` `/v1/workspaces/{workspaceId}/operations/{operationId}`  
Equivalent member: `client.GetHostedWorkspaceOperationAsync`  

#### Signature

```csharp
public Task GetHostedOperationAsync(
Guid workspaceId,
Guid operationId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `operationId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-7261-284a8b699ebd"
    },
    {
      "in": "path",
      "name": "operationId",
      "value": "00000000-0000-0000-5ba1-19fa55640b6d"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Workspaces.GetHostedOperationAsync(workspaceId: "00000000-0000-0000-7261-284a8b699ebd", operationId: "00000000-0000-0000-5ba1-19fa55640b6d");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIb3N0ZWRXb3Jrc3BhY2VPcGVyYXRpb24ifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJXb3Jrc3BhY2VzLkdldEhvc3RlZFNvdXJjZUFzeW5jIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0SG9zdGVkV29ya3NwYWNlU291cmNlIiwicGF0aCI6Ii92MS93b3Jrc3BhY2VzL3t3b3Jrc3BhY2VJZH0vc291cmNlIiwicmVzb3VyY2UiOiJXb3Jrc3BhY2VzIiwic2VjdGlvbl9zaGEyNTYiOiJjOTE2N2Q0ZDE4NTMyMTgxMTIyYjVmNWQzZmE0MzFmYzNiNzEzOGU1MWEyMDU0YjFmZWNkZDRmNTZiZjY1MDgxIiwic2lnbmF0dXJlX3NoYTI1NiI6IjQzN2YwOWJjZWI2ZGZlMWE3ZjI5YTg0YjIzMjNiMGU4NzFkMGFlYjAxODAwM2ZiY2Q3YjZiNDQyNDZiODkzY2YifQ -->
### `client.Workspaces.GetHostedSourceAsync`

Operation ID: `getHostedWorkspaceSource`  
Route: `GET` `/v1/workspaces/{workspaceId}/source`  
Equivalent member: `client.GetHostedWorkspaceSourceAsync`  

#### Signature

```csharp
public Task GetHostedSourceAsync(
Guid workspaceId,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-43c8-d895a22336ed"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Workspaces.GetHostedSourceAsync(workspaceId: "00000000-0000-0000-43c8-d895a22336ed");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIb3N0ZWRXb3Jrc3BhY2VTb3VyY2UifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJXb3Jrc3BhY2VzLkxpc3RIb3N0ZWRBc3luYyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RIb3N0ZWRXb3Jrc3BhY2VzIiwicGF0aCI6Ii92MS93b3Jrc3BhY2VzIiwicmVzb3VyY2UiOiJXb3Jrc3BhY2VzIiwic2VjdGlvbl9zaGEyNTYiOiI3NGU2NGE5N2UzOWRlNDYwOWMxZGFmODJlNDUwNjA2OTQxYmE3YTZlYzI4ZjMzOTk1YmI1N2JmODRlZTYzNmQxIiwic2lnbmF0dXJlX3NoYTI1NiI6ImYyMGExMTMyYTFhODc0OTQ0ZjliODcxNWExMjUzZGY4MTE5MjY1ZmFhNzA1ZDJjOGVkMDBlOTcyNjYyNmUyM2QifQ -->
### `client.Workspaces.ListHostedAsync`

Operation ID: `listHostedWorkspaces`  
Route: `GET` `/v1/workspaces`  
Equivalent member: `client.ListHostedWorkspacesAsync`  

#### Signature

```csharp
public Task ListHostedAsync(
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Workspaces.ListHostedAsync();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0SG9zdGVkV29ya3NwYWNlcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJXb3Jrc3BhY2VzLk9wZW5Ib3N0ZWRBc3luYyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJvcGVuSG9zdGVkV29ya3NwYWNlIiwicGF0aCI6Ii92MS93b3Jrc3BhY2VzIiwicmVzb3VyY2UiOiJXb3Jrc3BhY2VzIiwic2VjdGlvbl9zaGEyNTYiOiJiOGE3NjRjZjRkY2NkYTY1MTc1MmQ4YzhkZDJmM2U5NGNkMzg5ZWRjMWY2YTgxODg3NjAzZDFkYTFkYjAzNDhlIiwic2lnbmF0dXJlX3NoYTI1NiI6ImI0OTU4YzUzMTY4OTg5Yzk1OWI5Zjk3MTZmNmM4OTRmMzlhMGY3OWViNDdiZDJiOWU0MTBjYjYxYmZkY2I0YmQifQ -->
### `client.Workspaces.OpenHostedAsync`

Operation ID: `openHostedWorkspace`  
Route: `POST` `/v1/workspaces`  
Equivalent member: `client.OpenHostedWorkspaceAsync`  

#### Signature

```csharp
public Task OpenHostedAsync(
OpenHostedWorkspaceRequest body,
string? idempotencyKey = null,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `Idempotency-Key` | `header` | no | `string` | Required here or in the idempotencyKey body field. Replays never allocate or execute again. |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `201` | Prepared workspace; source and provider allocation recorded durably | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Workspaces.OpenHostedAsync(body: {}, /* optional: Idempotency-Key */);
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJvcGVuSG9zdGVkV29ya3NwYWNlIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJXb3Jrc3BhY2VzLlJlY292ZXJIb3N0ZWRBc3luYyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJyZWNvdmVySG9zdGVkV29ya3NwYWNlIiwicGF0aCI6Ii92MS93b3Jrc3BhY2VzL3t3b3Jrc3BhY2VJZH0vcmVjb3ZlciIsInJlc291cmNlIjoiV29ya3NwYWNlcyIsInNlY3Rpb25fc2hhMjU2IjoiYWFmMDc0OTU4NGQ4ZGJhN2MxOGE3YjA5ZjVjNzk2YTI5NTc1ZjBkMWRiOTg1N2U1YWRiOTU1YmUzM2JjZTEyZiIsInNpZ25hdHVyZV9zaGEyNTYiOiJmNjBkY2Q2ZWNkZDE4ZDI3Y2JlZTJiZDY2ODg3ZDFmNjJjYWNjODMyYjljZGI0NWVmNDc4YjliZWUxZGIzYjcxIn0 -->
### `client.Workspaces.RecoverHostedAsync`

Operation ID: `recoverHostedWorkspace`  
Route: `POST` `/v1/workspaces/{workspaceId}/recover`  
Equivalent member: `client.RecoverHostedWorkspaceAsync`  

#### Signature

```csharp
public Task RecoverHostedAsync(
Guid workspaceId,
RecoverHostedWorkspaceRequest body,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `202` | No verified terminal receipt yet; workspace remains unavailable for new commands | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "body": {
    "operationId": "00000000-0000-0000-d4ac-b0b84827b6d9"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-973a-c9ae0260973d"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Workspaces.RecoverHostedAsync(workspaceId: "00000000-0000-0000-973a-c9ae0260973d", body: {"operationId": "00000000-0000-0000-d4ac-b0b84827b6d9"});
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWNvdmVySG9zdGVkV29ya3NwYWNlIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJXb3Jrc3BhY2VzLlJ1bkhvc3RlZEFzeW5jIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InJ1bkhvc3RlZFdvcmtzcGFjZSIsInBhdGgiOiIvdjEvd29ya3NwYWNlcy97d29ya3NwYWNlSWR9L3J1biIsInJlc291cmNlIjoiV29ya3NwYWNlcyIsInNlY3Rpb25fc2hhMjU2IjoiOTk3YmJlYjVmZWFjODUwMWFjYzQ3NWJlOWRjNzVjMGFkNTA5NjBhYTI2MzhiNmRjMDk4OTNmNDBmOTgzZDY2MSIsInNpZ25hdHVyZV9zaGEyNTYiOiJkNTAwM2IzNjFkOTFkZGUzOTNkNzliMDA0MjE2MDM2ZWFhMjVkZmNiYTE4MDBhZGEyYTQ5NjU1MjU0ZjUwYzMzIn0 -->
### `client.Workspaces.RunHostedAsync`

Operation ID: `runHostedWorkspace`  
Route: `POST` `/v1/workspaces/{workspaceId}/run`  
Equivalent member: `client.RunHostedWorkspaceAsync`  

#### Signature

```csharp
public Task RunHostedAsync(
Guid workspaceId,
RunHostedWorkspaceRequest body,
string? idempotencyKey = null,
RequestOptions? requestOptions = null,
CancellationToken cancellationToken = default)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `Idempotency-Key` | `header` | no | `string` | Required here or in the idempotencyKey body field. Replays never allocate or execute again. |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `202` | Running or uncertain operation; inspect or explicitly recover, never resend with a new key | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "body": {
    "command": "example"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-4862-6c003dd1756b"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```csharp
var result = await client.Workspaces.RunHostedAsync(workspaceId: "00000000-0000-0000-4862-6c003dd1756b", body: {"command": "example"}, /* optional: Idempotency-Key */);
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJydW5Ib3N0ZWRXb3Jrc3BhY2UifQ -->

