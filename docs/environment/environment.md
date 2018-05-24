# 環境

作者：[@dvnabbott](https://twitter.com/dvnabbott)  
譯者：朱文藝

建立 React Native 的開發環境有兩個常見的的方法： `create-react-native-app` 以及 `react-native-cli`

## `create-react-native-app`

React Native 社群提供了一個叫做 `create-react-native-app` 命令列工具，能夠自動建立一個新的 React Native 專案，這是新手上路的最佳方法了。這個工具會協助產生一個 QR code，掃描了之後可以在自己的手機裝置上開啟 app。

當更新了程式碼後，手機裝置上的 app 也會隨之更新。然而你會需要先安裝一個名為 `Expo` 的 app，它是相當好用的 Ract Native 客戶端預覽 app。

這個辦法不是沒有缺點，它只能適用純粹的 JavaScript app。如果你的專案裡有使用客製化的原生模組 (Obj-C/Swift, Java 等等)，那麼你需要 `eject`。`create-react-native-app` 命令列工具提供 `eject` 指令，協助將 app 匯出為如同 `react-native init` 指令所生成的格式，如此這些原生的模組就可以運作了。

我們會在下一篇文章[「快速開始」](/environment/quick_start.md))裡提到更多。

## `react-native-cli`

如果你知道自己的 app 將會使用客製化的原生模組，那麼 `react-native-cli` 會是比較好的選擇。你可以到 Facebook 官方文件 [Getting Started](https://facebook.github.io/react-native/docs/getting-started.html) 得到更多資訊。
