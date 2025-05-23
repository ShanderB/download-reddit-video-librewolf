# Disclaimer
This extension is an unverified extension. To use following this guide, you need to use one of the supported versions:
[Firefox Extension Workshop](https://extensionworkshop.com/documentation/publish/signing-and-distribution-overview/#signing-your-addons)

# Redirect to Rapidsave Firefox/Librewolf

This browser extension allows you to quickly save Reddit posts using Rapidsave. When you click the extension button while on a Reddit page, it will automatically redirect you to Rapidsave, trigger the download, and close the tab as soon as the download starts.

## How to Build and Run

1. **Build the Extension**

   Use [web-ext](https://github.com/mozilla/web-ext) to build the extension package:

   ```sh
   npx web-ext build --overwrite-dest
   ```

   This will create a .zip file in the web-ext-artifacts directory. I already created a zip file for you, so you can skip this step if you want.
   The zip file will be named `redirect-to-rapidsave-<version>.zip`.

## Firefox Developer Setting

To install unsigned extensions in Firefox (for development purposes), you need to disable signature enforcement:

1. Open a new tab and go to: `about:config`
2. Search for: `xpinstall.signatures.required`
3. Double-click the preference to set it to `false`

This allows you to load and use your extension without needing it to be signed by Mozilla.

## Install the Extension Temporarily
1. Open Firefox and go to `about:debugging#/runtime/this-firefox`.
2. Click on "Load Temporary Add-on".
3. Select the `manifest.json` file from your extension directory.
4. The extension will be loaded temporarily and will be available for use until you restart Firefox.

## Install the Extension Permanently
1. Open Firefox and go to `about:addons`.
2. Click on the gear icon in the top right corner and select "Install Add-on From File...".
    - You can also drag and drop the .zip file into the Firefox add-ons page to install it.
3. Select the .zip file you created in the `web-ext-artifacts` directory.
4. The extension will be installed and will appear in your list of add-ons with the message ``Redirect to Rapidsave could not be verified for use in LibreWolf. Proceed with caution.``.

## How It Works

- When you are on a Reddit page and click the extension button:
  1. The extension checks if the current tab URL contains "reddit.com".
  2. It opens a new tab with Rapidsave, passing the Reddit post URL.
  3. If the Rapidsave page is protected by Cloudflare (captcha. Usually when using incognito), the extension waits until you solve the captcha and the Rapidsave page loads.
  4. Once the Rapidsave page loads, the extension automatically clicks the download button for you.
  5. The Rapidsave tab will close automatically as soon as the download starts.

## Permissions

The extension requires the following permissions:

- Access to tabs and activeTab.
- Access to rapidsave.com to automate the download process.
- Access to downloads to detect when the download starts.

## Icons

Icons are provided in the images directory for various sizes.