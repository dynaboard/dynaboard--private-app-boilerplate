## Demo
View a live demo of the template [here](https://private-app-demo.dynaboard.app/auth).

## How to Use this Template
This template provides all of the basics for building a private application that requires user login. You’ll need to configure a few things to get started, but once configured, you’ll be able to make a private app with as many pages as you’d like by right clicking on the `index` page and clicking duplicate.

&nbsp;

### Steps to get started
While it’s possible (and encouraged!) to deploy this template right away (by clicking the rocketship at the top right of this window), you’ll be missing out on a few things until you complete the steps below.

1. **Remove or update the GitHub auth resource** with your own client ID and secret. It wont work correctly until the information is updated or the resource is removed.
2. **Update the index page** with your own content, but before you do, make sure to checkout the `getUserInfo` function and the `userInfoExample` page for examples on how to retrieve and display user session information. *Note: To see any user info you'll need to login to the application itself. You can do this in the editor by navigating to the `/auth` page switching to "Interact" mode using `CMD / CTRL + ALT` and logging into the app with your email.*
3. **Update the auth page** with your own application name and logo.
4. (Optional) If this application is going to be an internal application, you’ll want to **update the sign-in rules** under the settings page to use the `Email Domain is in` rule with `your-domain.com` to keep anyone without your corporate email from logging in. You can also use the `Email is in` rule if you only want to allow a few specific people.
5. **Remove the "View README"** button in the header by navigating to the "Components" tab on the left side of the screen and deleting the `readmeButton` from the `pageHeader` component.
6. **Delete this README**. It’s fully public, so we strongly suggest deleting it before publishing your application. Or, if you’d like to practice editing authorization rules, you can make this page private by deleting the auth rule overrides from this specific page as the application default rules set all pages to require login.
7. **Delete the `userInfoExample` page** or customize it for your use-case.
8. **Deploy your new app!**

&nbsp;

## Additional Reference

&nbsp;

### Pages

- `index`: This is the main page of your application. You should always have a page named `index`, but feel free to update it however you want. This is also the page you’ll want to duplicate when making new pages for your application!
- `auth`: This is your sign-in page. If users are not logged in, they will be redirected here from any other private page. If they are logged in, they’ll automatically be redirected to the index page.
- `userInfoExample`: We’ve included some example components and code to show you how to get and display user session info.
- `README`: That’s this page! Feel free to delete it when you’re ready to go live.

&nbsp;

### Authentication & Authorization

Rules related to authentication and authorization can be found in two different places. Sign-in and default authorization rules for the entire app can be found at the bottom of the left side-bar under `Settings`. Authorization rules for individual pages can be found for the currently selected page in the right-hand side properties panel under `Authorization`.

&nbsp;

#### Default Configuration

The default authorization configuration for this template consists of three rules:
1. If user is authenticated then allow.
2. If user is unauthenticated then redirect to `/auth`.
3. Everyone else deny.

&nbsp;

Since this configuration is inherited by every page in the application, we don’t need to specify any additional rules on pages that we want to be private. However, you’ll notice that since the `/auth` page is public, it does overwrite these rules with a rule set that is nearly inverse:
1. If user is authenticated then redirect to `/`.
2. If user is unauthenticated then allow`.
3. Everyone else deny.

&nbsp;

#### Creating A Sign-in Rule
While the default auth rules make sure that someone is authenticated, they don’t care who exactly gets let into the app. This is where sign-in rules come into play. As mentioned in the steps to get started, you’ll want to update the sign-in rules to either use the `Email Domain is in` rule with `your-domain.com` or `Email is in` rule.

&nbsp;

#### Configuring Resources
Many additional authentication resources are available for you to use including: Google, Facebook, Okta, Microsoft (Azure AD), or any spec compliant OIDC provider. However, we’ve included the One-time PIN and GitHub resources in this boilerplate due to their relative ease of configuration.
- **One-time PIN**: Doesn’t require any additional configuration and uses the same infrastructure we use for our own logins (without users needing a Dynaboard account) to validate user emails.
- **GitHub**: apps can easily be created and configured under Settings > Developer Setting > OAuth Apps in the GitHub dashboard. 