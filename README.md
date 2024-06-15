# power-bi-jira-api

```dax
##JiraAPIFunction
let
  JiraAPIFunction = (projectKey A text, startAt as number) as record =>
  let
    BaseUrl = "https://<domain>.atlassian.net/rest/api/3/search?jql=project=" & projectKey & "&maxResults=1000&startAt=" & Number.ToText(startAt),
    Headers = [Authorization = "Basic " & Binary.ToText(Text.ToBinary("<email@domain.com>:<Ira_API_Token>"), BinaryEncoding.Base64)],
    Source = Json.Document(Web.Contents(baseUrl, [Headers = Headers]))
  in
    Source
in
  JiraFunction
```
