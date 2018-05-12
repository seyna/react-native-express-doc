# React Native Express 中文手冊

<div style="text-align:right;">文件最近更新時間； 2018/05/13</div>

?> 文件尚在翻譯當中，預計會在 2018 年 7 月翻譯完畢。

## 學習 React Native

作者：[@dvnabbott](https://twitter.com/dvnabbott)  
譯者：朱文藝

React Native 是一個幫助你打造跨平台 app 的框架工具。

用 React Native 打造 app 非常有效率，也很讓人上癮 ─ 但要上手卻有一點點門檻。你可以將這裡視為 Facebook 官方文件的輔助文件。

Facebook 的手冊，某種程度假設讀者都有一些使用 React 開發網站的知識。如果你遇到一些並不徹底了解的主題，比如 Babel 怎麼運作的，那麼這份手冊裡的範例將可以加快你學習的速度。

這份手冊也會涵蓋相關的主題，比如說 Redux (它並沒有在 React Native 官方文件裡被提到。)

我希望你享受學習 React Native 的過程。你可以在 twitter 找到我，[@dvnabbott](https://twitter.com/dvnabbott)  ，留言提到你遇到的問題。有一些內容是其他作者寫的 (頁面上方有紀錄)，也歡迎去找他們。

## Hello World

當你新建了一個 React Native app，它看起來會像是這樣：

```javascript
/**
 * Sample React Native App
 * https://github.com/facebook/react-native
 * @flow
 */

import React, { Component } from 'react';
import {
  AppRegistry,
  StyleSheet,
  Text,
  View
} from 'react-native';

export default class Project extends Component {
  render() {
    return (
      <View style={styles.container}>
        <Text style={styles.welcome}>
          Welcome to React Native!
        </Text>
        <Text style={styles.instructions}>
          To get started, edit index.ios.js
        </Text>
        <Text style={styles.instructions}>
          Press Cmd+R to reload,{'\n'}
          Cmd+D or shake for dev menu
        </Text>
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
  },
  welcome: {
    fontSize: 20,
    textAlign: 'center',
    margin: 10,
  },
  instructions: {
    textAlign: 'center',
    color: '#333333',
    marginBottom: 5,
  },
});

AppRegistry.registerComponent('Project', () => Project);
```


![](https://www.dropbox.com/s/l84jh4z3kam6t3d/new_app.png?raw=1)

你可能會發現上面的程式碼看起來不太像你現在所寫的 JavaScript。這是因為它的是最新的功能 (ES6 imports, classes, block-scoped variable declarations)，以及 JSX 延伸。

在接下來的段落裡，我會對這每一個主題做簡單的說明，如果你已經熟悉這些主題了，請自行跳過囉。這份文件裡大部分的段落都是彼此獨立的。

喔對了，首先讓我們來設置 React Native 的開發環境吧！