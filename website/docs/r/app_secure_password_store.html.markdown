---
layout: 'okta'
page_title: 'Okta: okta_app_secure_password_store'
sidebar_current: 'docs-okta-resource-app-secure-password-store'
description: |-
  Creates a Secure Password Store Application.
---

# okta_app_secure_password_store

This resource allows you to create and configure a Secure Password Store Application.

## Example Usage

```hcl
resource "okta_app_secure_password_store" "example" {
  label              = "example"
  username_field     = "user"
  password_field     = "pass"
  url                = "https://test.com"
  credentials_scheme = "ADMIN_SETS_CREDENTIALS"
}
```

## Argument Reference

The following arguments are supported:

- `label` - (Required) The display name of the Application.

- `password_field` - (Required) Login password field.

- `username_field` - (Required) Login username field.

- `url` - (Required) Login URL.

- `optional_field1` - (Optional) Name of optional param in the login form.

- `optional_field1_value` - (Optional) Name of optional value in the login form.

- `optional_field2` - (Optional) Name of optional param in the login form.

- `optional_field2_value` - (Optional) Name of optional value in the login form.

- `optional_field3` - (Optional) Name of optional param in the login form.

- `optional_field3_value` - (Optional) Name of optional value in the login form.

- `credentials_scheme` - (Optional) Application credentials scheme. Can be set to `"EDIT_USERNAME_AND_PASSWORD"`, `"ADMIN_SETS_CREDENTIALS"`, `"EDIT_PASSWORD_ONLY"`, `"EXTERNAL_PASSWORD_SYNC"`, or `"SHARED_USERNAME_AND_PASSWORD"`.

- `reveal_password` - (Optional) Allow user to reveal password. It can not be set to `true` if `credentials_scheme` is `"ADMIN_SETS_CREDENTIALS"`, `"SHARED_USERNAME_AND_PASSWORD"` or `"EXTERNAL_PASSWORD_SYNC"`.

- `shared_username` - (Optional) Shared username, required for certain schemes.

- `shared_password` - (Optional) Shared password, required for certain schemes.

- `users` - (Optional) The users assigned to the application. See `okta_app_user` for a more flexible approach.
  - `DEPRECATED`: Please replace usage with the `okta_app_user` resource.

- `groups` - (Optional) Groups associated with the application. See `okta_app_group_assignment` for a more flexible approach.
  - `DEPRECATED`: Please replace usage with the `okta_app_group_assignments` (or `okta_app_group_assignment`) resource.

- `status` - (Optional) Status of application. By default, it is `"ACTIVE"`.

- `accessibility_error_redirect_url` - (Optional) Custom error page URL.

- `accessibility_login_redirect_url` - (Optional) Custom login page for this application.

- `accessibility_self_service` - (Optional) Enable self-service. By default, it is `false`.

- `auto_submit_toolbar` - (Optional) Display auto submit toolbar.

- `hide_ios` - (Optional) Do not display application icon on mobile app.

- `hide_web` - (Optional) Do not display application icon to users.

- `skip_users` - (Optional) Indicator that allows the app to skip `users` sync (it's also can be provided during import). Default is `false`.

- `skip_groups` - (Optional) Indicator that allows the app to skip `groups` sync (it's also can be provided during import). Default is `false`.

## Attributes Reference

- `name` - Name assigned to the application by Okta.

- `sign_on_mode` - Sign-on mode of application.

- `user_name_template` - The default username assigned to each user.

- `user_name_template_type` - The Username template type.

## Import

Secure Password Store Application can be imported via the Okta ID.

```
$ terraform import okta_app_secure_password_store.example <app id>
```

It's also possible to import app without groups or/and users. In this case ID may look like this:

```
$ terraform import okta_app_basic_auth.example <app id>/skip_users

$ terraform import okta_app_basic_auth.example <app id>/skip_users/skip_groups

$ terraform import okta_app_basic_auth.example <app id>/skip_groups
```
