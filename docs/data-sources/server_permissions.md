---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "mssql_server_permissions Data Source - terraform-provider-mssql"
subcategory: ""
description: |-
  Returns all permissions grated to given principal
---

# mssql_server_permissions (Data Source)

Returns all permissions grated to given principal

## Example Usage

```terraform
data "mssql_sql_login" "example" {
  name = "example_login"
}

data "mssql_server_permissions" "example" {
  principal_id = data.mssql_sql_login.example.principal_id
}

output "permissions" {
  value = data.mssql_server_permissions.example.permissions
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `principal_id` (String) ID of the principal who will be granted `permission`. Can be retrieved using `mssql_server_role` or `mssql_sql_login`.

### Read-Only

- `id` (String) Equals to `principal_id`.
- `permissions` (Attributes Set) Set of permissions granted to the principal (see [below for nested schema](#nestedatt--permissions))

<a id="nestedatt--permissions"></a>
### Nested Schema for `permissions`

Read-Only:

- `permission` (String) Name of server-level SQL permission. For full list of supported permissions see [docs](https://learn.microsoft.com/en-us/sql/t-sql/statements/grant-server-permissions-transact-sql?view=azuresqldb-current#remarks)
- `with_grant_option` (Boolean) When set to `true`, `principal_id` will be allowed to grant the `permission` to other principals.

