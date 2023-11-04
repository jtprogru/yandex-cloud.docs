You can assign a role for a group as a resource. You can grant roles to users and groups from your organization.

For example, allow a user to view group information and manage its members.

{% list tabs %}

- Cloud Organization

   1. [Log in]({{ link-passport-login }}) to the organization administrator account.

   1. Go to [{{org-full-name}}]({{ link-org-main }}).

   1. In the left-hand panel, select **{{ ui-key.yacloud_org.pages.groups }}** ![icon-services](../../_assets/organization/icon-groups.svg) and click the line with the group name.

   1. Go to the **{{ ui-key.yacloud_org.entity.group.title_tab-access }}** tab.

   1. Click **{{ ui-key.yacloud_org.entity.group.action_add-acl }}**.

   1. Click **{{ ui-key.yacloud.component.acl.update-dialog.button_select-subject }}**.

   1. Select the appropriate user or group from the list or use the search.

   1. Click **{{ ui-key.yacloud.component.acl.update-dialog.button_add-role }}** and select `organization-manager.groups.memberAdmin`.

   1. Click **{{ ui-key.yacloud.common.save }}**.

   The user will appear in the list of group access bindings.

{% endlist %}
