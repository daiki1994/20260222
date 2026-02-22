## サービスプリンシパル登録
Azure認証情報（サービスプリンシパル）の登録

```bash
az ad sp create-for-rbac --name "ToDoAppDeployAuth" --role contributor `
--scopes /subscriptions/31a1e269-7840-4c72-94fa-a3edf6e76551/resourceGroups/rg-udemytodoappmoto/providers/Microsoft.Web/sites/rg-udemytodoappmoto `
--json-auth
```
```
az ad sp create-for-rbac `
  --name "ToDoAppDeployAuth" `
  --role contributor `
  --scopes /subscriptions/31a1e269-7840-4c72-94fa-a3edf6e76551/resourceGroups/rg-udemytodoappmoto/providers/Microsoft.Web/sites/udemytodoappmoto-app `
  --sdk-auth
```
notify-serviceへの権限付与
```bash
az role assignment create `
  --assignee サービスプリンシパルのクライアントID `
  --role contributor `
  --scope /subscriptions/31a1e269-7840-4c72-94fa-a3edf6e76551/resourceGroups/rg-udemytodoappmoto/providers/Microsoft.Web/sites/udemytodoapp-notify
```

ACR への AcrPush 権限付与
```bash
az role assignment create `
  --assignee 7f418716-4ef3-4342-9746-c4180950a129 `
  --role AcrPush `
  --scope /subscriptions/31a1e269-7840-4c72-94fa-a3edf6e76551/resourceGroups/rg-udemytodoappmoto/providers/Microsoft.ContainerRegistry/registries/udemytodoappmotoacr01
```


出力されるJSONをメモしておきます。


GitHub Secretsに登録
![alt text](image.png)

AZURE_CREDENTIALS
![alt text](image-1.png)


ACR_NAMEも登録
udemytodoappacr01
![alt text](image-2.png)


RESOURCE_GROUPも登録
rg-udemytodoappmoto


![alt text](image-3.png)