# {{ GL }}

## Setting up a link {#relation}


In [{{ tracker-name }} issues](../about-tracker.md#zadacha), you can automatically add links to [Merge Requests]({{ gl.docs }}/ee/user/project/merge_requests/) from {{ GL }}. To do this, specify the appropriate issue's [key](../glossary.md#key) in the name or description of a new Merge Request. The links will be placed in [{{ ui-key.startrek.ui_components_issue-links_ExternalLinksCollapse.external-relations}}](../external-links.md).

You can also enable automatic creation of issue comments with information about Merge Requests. Auto comments are only available for [{{ mgl-name }}](../../managed-gitlab/).

{% include [create hook](../../_includes/managed-gitlab/create-hook.md) %}

{% include [test hook](../../_includes/managed-gitlab/test-hook.md) %}

### See also {#see-also}

* [Manual for integrating {{ GL }} with {{ tracker-full-name }}](../../managed-gitlab/tutorials/tracker-integration.md)

## Connecting a repository {#repo}

To connect your repository on [GitLab](https://gitlab.com) to {{ tracker-name }}:

{% note info %}

Private repositories can only be accessed by users logged in to GitLab (**Internal project**) or the project team (**Private project**).

{% endnote %}

1. {% include [make sure you are admin](../../_includes/tracker/make-sure-admin.md) %}

1. {% include [path to the repository](../../_includes/tracker/repository-path.md) %}

1. Choose GitLab in the **{{ ui-key.startrek.blocks-desktop_repository-modal.platform }}** field.

1. Get an OAuth token for your repository on GitHub:

   - Log in to GitLab.

   - Click on your picture in the upper-right corner and choose **Settings**.

   - On the left-hand panel, select **Access Tokens**.

   - Enter a name for the token in the **Name** field.

   - Set the token expiration date in the **Expires at** field.

   - Configure the token's access rights. For {{ tracker-name }} to operate properly, make sure to enable the **api** option.

      ![](../../_assets/tracker/gitlab-token-settings.png)

   - Click **Create personal access token**.

   - Copy a token to the clipboard.

      {% note alert %}

      The token value is displayed only once. If you close the page, you will not be able to view it again.

      {% endnote %}

1. Enter the repository address in the `https://gitlab.com/<repository owner login>/<repository name>` format and specify the access token.

1. Click **{{ ui-key.startrek.blocks-desktop_repository-modal.button--connect }}**.

1. Make sure that the repository status in {{ tracker-name }} is **{{ ui-key.startrek.blocks-desktop_page-admin-tab_type_repositories.status--success }}**.

To link a commit to an issue in {{ tracker-name }}, specify the issue key in the comments for the commit. You can view the linked commits:

- In the **{{ ui-key.startrek-backend.fields.issue.commits-key-value }}** tab on the issue page.
- In the **{{ ui-key.startrek.blocks-desktop_b-page_type_queue.tab_commits }}** tab on the queue page.

If the **{{ ui-key.startrek.blocks-desktop_b-page_type_queue.tab_commits }}** tab is missing, make sure it is enabled in your [queue settings](../manager/edit-queue-general.md#ul_gcz_xlp_m2b).

## Own server {#on-premise}

{% include [on-premise server](../../_includes/tracker/on-premise-server.md) %}

