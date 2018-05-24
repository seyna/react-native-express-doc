# 快速開始

作者：[@jimmyliu](https://twitter.com/jimmyliu)  
譯者：朱文藝

建立一個新的 React Native 專案很容易

我們需先安裝 Node.js。如果你還沒有安裝，請到 [nodejs.org](https://nodejs.org/en/download/) 下載，依據你的平台選擇適當的版本，並且依據說明安裝完畢。

## 安裝

首先，我們先安裝 `create-react-native-app` (CRNA)。[CRNA](https://github.com/react-community/create-react-native-app) 是一個協助輕易建立 React Native 專案的命令列工具。

```
npm install -g create-react-native-app
```

之後我們用它建立 app

```
create-react-native-app my-app
cd my-app/
npm start
```

這會花上一段時間，因為 CRNA 要下載所有的相關函式庫。完畢之後你應該會看到這個有 QR code 的畫面

![](https://www.dropbox.com/s/cpmjtwdnxltheva/createnativeapp.png?raw=1)

你已經建立了屬於你的第一支 React Native app！現在你可以在手機裡安裝 Expo app，並且掃描 QR code 以預覽它

如果看到底下的畫面，那就代表成功了，恭喜！接下來你可以繼續工作了

![](https://www.dropbox.com/s/wycoj84pwvq1x5e/expo.png?raw=1)

## 修改

試著改變 `App.js` 裡的文字，存檔，看看裝置裡的 app 有沒有隨著改變

## 接下來

現在你已經將專案建置妥當，讓我們開始學習 JavaScript 裡頭你將會使用的重要功能吧。如果你已經熟悉它們了，可以跳過至 [Components](http://www.reactnativeexpress.com/components) 以了解 React 元件以及元件的生命週期。

如果你已經熟悉 React，也可以跳到 [Core Components](http://www.reactnativeexpress.com/core_components) 學習 React Native 搭載的核心元件。