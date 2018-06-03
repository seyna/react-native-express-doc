# Component API

作者：[@dvnabbott](https://twitter.com/dvnabbott)  
譯者：朱文藝

## `this.props`

`Components` 可以藉由傳遞到了 `constructor` 裡的參數執行初始化設定。這些參數稱為 `props`。`props` 可以藉由元件裡的 `this.props` 取得，你可以接著使用它們以改變元件的顯示或者行為。然而 `props` 不能夠在元件的 methods 裡被修改。

父元件可能會想要改變子元件的 `props`。子元件一般來說會重新顯示自身以顯示變更參數後的新狀態。子元件也可能會決定不重新顯示，這可以在 `shouldComponentUpdate()` 辦法裡設定。(我們會在元件的生命週期 API 裡提到更多)

## `this.state`

`Components` 可以透過物件 `state` 保存現在的狀態。元件裡的 methods 皆可以透過 `this.state` 取出狀態。不像 `props`，父元件並不能取得子元件的 `state`，因為它本來就是為了紀錄自身內部的狀態，而非為了外部的設定。

有一點非常值得注意，就是你並不能透過直接賦值的方式改變 `state` 物件。比如說這樣 `this.state.foo = 'bar'` 是會失敗的，相對的，你應該要使用 `this.setState()` 辦法。

## `this.setState(Object newState)`

`Components` 可以透過 `this.setState()` 以更新 `state`。所有傳遞的 keys 都會合併，並覆寫原本的 keys，一同進入 `this.state`。

## 例子

下面的是一個計數器的例子，裏頭的 `Counter` 元件會將流逝的時間記錄為 `state.count`。`App` 元件用兩個 `props`：`size` 與 `color` 顯示 `Counter` 元件。`App` 可以輕易地顯示多個不同大小與顏色的計數器。

<iframe frameborder="0" allowfullscreen="" src="https://cdn.rawgit.com/dabbott/react-native-web-player/gh-v2.0.0-alpha.3/index.html#code=import%20React%2C%20%7B%20Component%20%7D%20from%20'react'%0Aimport%20%7B%20AppRegistry%2C%20View%2C%20Text%2C%20StyleSheet%20%7D%20from%20'react-native'%0A%0Aclass%20Counter%20extends%20Component%20%7B%0A%0A%20%20state%20%3D%20%7Bcount%3A%200%7D%0A%0A%20%20componentDidMount()%20%7B%0A%20%20%20%20setInterval(()%20%3D%3E%20%7B%0A%20%20%20%20%20%20this.setState(%7Bcount%3A%20this.state.count%20%2B%201%7D)%0A%20%20%20%20%7D%2C%201000)%0A%20%20%7D%0A%0A%20%20render()%20%7B%0A%20%20%20%20const%20%7Bcount%7D%20%3D%20this.state%0A%20%20%20%20const%20%7Bcolor%2C%20size%7D%20%3D%20this.props%0A%0A%20%20%20%20return%20(%0A%20%20%20%20%20%20%3CText%20style%3D%7B%7Bcolor%2C%20fontSize%3A%20size%7D%7D%3E%0A%20%20%20%20%20%20%20%20%7Bcount%7D%0A%20%20%20%20%20%20%3C%2FText%3E%0A%20%20%20%20)%0A%20%20%7D%0A%7D%0A%0Aexport%20default%20class%20App%20extends%20Component%20%7B%0A%20%20render()%20%7B%0A%20%20%20%20return%20(%0A%20%20%20%20%20%20%3CView%20style%3D%7Bstyles.container%7D%3E%0A%20%20%20%20%20%20%20%20%3CCounter%20color%3D%7B'lightblue'%7D%20size%3D%7B16%7D%20%2F%3E%0A%20%20%20%20%20%20%20%20%3CCounter%20color%3D%7B'skyblue'%7D%20size%3D%7B32%7D%20%2F%3E%0A%20%20%20%20%20%20%20%20%3CCounter%20color%3D%7B'steelblue'%7D%20size%3D%7B80%7D%20%2F%3E%0A%20%20%20%20%20%20%20%20%3CCounter%20color%3D%7B'darkblue'%7D%20size%3D%7B140%7D%20%2F%3E%0A%20%20%20%20%20%20%3C%2FView%3E%0A%20%20%20%20)%0A%20%20%7D%0A%7D%0A%0Aconst%20styles%20%3D%20StyleSheet.create(%7B%0A%20%20container%3A%20%7B%0A%20%20%20%20flex%3A%201%2C%0A%20%20%20%20justifyContent%3A%20'center'%2C%0A%20%20%20%20alignItems%3A%20'center'%2C%0A%20%20%7D%2C%0A%7D)%0A%0AAppRegistry.registerComponent('App'%2C%20()%20%3D%3E%20App)%0A&amp;width=260&amp;scale=0.75&amp;fullscreen=true&amp;styles=%7B%22tab%22%3A%7B%22backgroundColor%22%3A%22rgb(250%2C250%2C250)%22%7D%2C%22header%22%3A%7B%22backgroundColor%22%3A%22rgb(250%2C250%2C250)%22%2C%22boxShadow%22%3A%22rgba(0%2C%200%2C%200%2C%200.2)%200px%201px%201px%22%2C%22zIndex%22%3A10%7D%2C%22headerText%22%3A%7B%22color%22%3A%22%23AAA%22%2C%22fontWeight%22%3A%22normal%22%7D%2C%22transpilerHeader%22%3A%7B%22backgroundColor%22%3A%22rgb(240%2C240%2C240)%22%2C%22boxShadow%22%3A%22rgba(0%2C%200%2C%200%2C%200.2)%200px%201px%201px%22%2C%22zIndex%22%3A10%7D%2C%22transpilerHeaderText%22%3A%7B%22color%22%3A%22%23888%22%2C%22fontWeight%22%3A%22normal%22%7D%2C%22tabText%22%3A%7B%22color%22%3A%22%23AAA%22%7D%2C%22tabTextActive%22%3A%7B%22color%22%3A%22%23000%22%7D%7D&amp;panes=%5B%22editor%22%2C%22player%22%5D" style="width: 100%; height: 800px;"></iframe>