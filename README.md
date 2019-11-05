# [Not Maintained] React Native AppUpdate

Sorry, guys. I haven't developed React Native since a long time ago, so this repo is no longer maintained.

If you still need this functionality, you can use [react-native-update-apk](https://github.com/mikehardy/react-native-update-apk) instead.

---

Update apk and update from app store in React Native.

## Installation
```bash
npm install react-native-appupdate --save
```
**Note: If your react-native version < 0.40**

```bash
npm install react-native-appupdate@1.0.5 --save
```

adding automatically with react-native link

```bash
react-native link react-native-appupdate
react-native link react-native-fs
```
## Usage
```javascript
import { Alert } from 'react-native';
import AppUpdate from 'react-native-appupdate';

const appUpdate = new AppUpdate({
  iosAppId: '123456',
  apkVersionUrl: 'https://github.com/version.json',
  needUpdateApp: (needUpdate) => {
    Alert.alert(
      'Update tip',
      'Finding new version, do you want to update?',
      [
        {text: 'Cancel', onPress: () => {}},
        {text: 'Update', onPress: () => needUpdate(true)}
      ]
    );
  },
  forceUpdateApp: () => {
    console.log("Force update will start")
  },
  notNeedUpdateApp: () => {
    console.log("App is up to date")
  },
  downloadApkStart: () => { console.log("Start") },
  downloadApkProgress: (progress) => { console.log(`Downloading ${progress}%...`) },
  downloadApkEnd: () => { console.log("End") },
  onError: () => { console.log("downloadApkError") }
});
appUpdate.checkUpdate();
```

```javascript
// version.json
{
  "versionName":"1.0.0",
  "apkUrl":"https://github.com/NewApp.apk",
  "forceUpdate": false
}
```
## Third Library
* react-native-fs
