---
title: — Basic Auth
order: 4
layout: post-toc
redirect_from: /docs/
---

# Authentication — Basic Auth

Basic Authentication lets you connect APIs to Zapier that authenticate users with a username and password. In a Zapier integration with Basic Auth, Zapier includes the name and password of the user in the API request bundle every time Zapier polls an API endpoint for new data or posts new data to an API endpoint.

![Zapier basic auth for users](https://cdn.zapier.com/storage/photos/8987788036a5a70072c9e75c4911ff6a.png)
_Example Basic Auth screen for users inside Zapier_

When you add Basic Auth to your integration, Zapier adds a pre-built form that requests a username and password whenever users authenticate with your API. Zapier then makes a test call to verify the credentials, and stores them to use with every subsequent API call Zapier makes to your app on behalf of the user. 

> **When to use Basic Auth:** Use Basic Auth if your API requires a username and password or other basic fields, needs no special configuration, and specifically if your API leverages "[HTTP Basic Authentication](https://en.wikipedia.org/wiki/Basic_access_authentication)". If you need further customization of your login flow or need additional data from users, [API key authentication](https://platform.zapier.com/docs/apikey) may be what your API requires.

<a id="add"></a>
## How to Add Basic Auth to a Zapier Integration

![Add Basic Auth to Zapier integration](https://cdn.zappy.app/a8f5698b7c1fd2556eb6b6dc0a983155.png)

To add Basic Auth to your Zapier integration, open the _Authentication_ tab in Zapier visual builder and select _Basic Auth_.

![Basic Auth settings](https://cdn.zappy.app/84f49570f1a21f2304d1f6dbcc9bbfc9.png)

Zapier automatically adds a form where users will enter their username and password, so you don't need to configure anything for core basic auth. 

All you need to add is a test API call where Zapier can verify that the credentials work, and optionally a connection label to help users identify the account.

<a id="form"></a>

## Add More Fields to a Basic Auth Input Form

![Add fields to Basic Auth Zapier](https://cdn.zappy.app/c17e6838cf27ed5704f561c75625864f.png)

In addition to the username and password on the pre-built form, you can add more fields if your API documentation requires it.

For each field that you need, click the _Add Fields_ button and fill in the details for your field.

![Zapier Basic Auth Input Form](https://cdn.zappy.app/f4346b3456ea0080862db2eae7108050.png)

Every input field requires a _Key_, the name your API uses to reference this field. Enter the same key name that your API uses.

Then fill in the optional fields, as appropriate, especially the _Label_:

- **Label**: A human-friendly name for this field. Enter what this value is called inside your app's UI.
- **Is this field required**: Check this box for your field, and for any other fields that your API requires for authentication.
- **Type**: Zapier uses the `string` text field for all input fields by default; select `password` instead if you would like to obscure the data as users enter it.
- **Help Text**: Include details to assist users in authenticating with your app, especially if they may be unsure where to find the data needed. Format text with [Markdown](https://zapier.com/blog/beginner-ultimate-guide-markdown/), and include a link if needed.
- **Default Value**: Include a value for this field to be used as a fallback. For optional fields, the default value is set on initial creation and used instead of missing or null values every time the Zap runs. For required fields, this value is used during Zap creation, but not when the Zap runs (Zapier raises an error for missing/null values instead).
- **Static Dropdown**: Include values to offer users pre-set options to choose from. [Learn more](https://platform.zapier.com/docs/input-designer#dropdown).

> **Note:** The input field designer also includes an option for computed fields; those are not applicable to Basic Auth login and are only used with OAuth v2 and Session auth.

Once you've added your input fields, Zapier lists each input field with its label, key, type, and required status on your authentication settings. Click the field to edit it, or click the gear icon and select _Delete_ to remove a field.

![Edit Basic Auth input fields](https://cdn.zappy.app/a207e9be179e401dadfa9d5422e4df5c.png)

When you've added the needed fields, click _Continue_ to Configure a Test Request & Connection Label and continue setting up your app's authentication.

<a id="test_request"></a>
## Configure a Test Request

For the test API call, enter an API endpoint under the _Test_ header where Zapier can test users' credentials for your app, and set the correct call method (typically `GET`). Use an API endpoint that does not require any additional details or configuration, such as `/me` or `/user` to simply check the app authentication and retrieve details about the user.

![Basic Auth configuration in Zapier](https://cdn.zappy.app/a910a8114e18b545a93bf1e2e735e5a1.png)

If your API requires any custom details in the API call, click the _Show Options_ link in the lower right, then add URL params or HTTP headers if needed.

![Zapier Basic Auth code mode](https://cdn.zappy.app/6ec17f1acd3def0addad6dfc9167acec.png)

If you need more customization, you can write custom JavaScript code to call your API and parse the output data. To do that, click the _Switch to Code Mode_ toggle. The first time you click the toggle, Zapier will convert the data from your API call form to JavaScript. If you switch back to form mode, Zapier will save your custom code but will not use it in the API call. Additionally, if you switch back to code mode again later, Zapier will not add any changes from the API call form to your code.

<a id="label"></a>
## Configure a Connection Label

![Zapier Basic Auth connection label](https://cdn.zappy.app/59307becaf617dca08115fa55477dffb.png)

Finally, add a connection label to your Zapier integration. Zapier always includes the app's name in each account label. You can additionally include:

- Plain text that will be included in every account connection
- Any information that users enter in the Zapier authentication form when adding your app, such as the username
- Output fields from your app's authentication test API call

Fields can be referenced using double curly braces. For example, the `username` field would look like {% raw %}`{{username}}`{% endraw %}. 

Learn more in our [Connection Label documentation](https://platform.zapier.com/docs/auth#label).

Click _Save & Continue_ when finished to save your authentication settings.

Then, test your authentication, adding a real account to ensure Zapier can successfully connect to your app and use your test API call. Check our [Authentication Testing docs](https://platform.zapier.com/docs/auth#test) for more details, common errors you may encounter, and how to resolve those.
