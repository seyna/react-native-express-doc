# 生命週期 API

作者：[@dvnabbott](https://twitter.com/dvnabbott)  
譯者：朱文藝

元件有自己的生命周期：初始、裝載、顯現、更新、卸載，以及移除。

這個生命週期可以協助管理不同平台(iOS、Android) API 的複雜度，並且提供一個簡單又一致的抽象層。這個生命週期也有助於你在不同的階段裡執行客製化的程式碼，以對顯示結果有更細緻的掌握。

讓我們來看看這些生命週期吧

## 裝載週期

`constrctor(object props)`

元件初始化的階段。傳遞到 `constructor` 的參數會是元件最開始的 `props`，而這通常會是來自於父元件。你可以視需要透過設定 `this.state` 指定初始的狀態。在這個階段裡，原生的 UI 都還不會被生成。

<br>

`componentWillMount()`

這個辦法只會被啟用一次，發生在第一次呈現畫面之前。在這個階段裡，同樣地，原生的 UI 都還不會被生成。

?> 編者：這個階段裡我通常會用來取得外部資料，比如 API 的 data feed，以生成畫面裡的清單

<br>

`render() -> React Element`

這個 render 辦法必須要回傳一個 React 物件以呈現些什麼 (null 的話就是什麼也不會呈現)

<br>

`componentDidMount()`

這個辦法只會被啟用一次，發生在第一次畫面生成之後。在這個階段，所有的原生 UI 都已經顯示完成了，而且可以透過 `this.refs` 以直接操作。如果你想要執行一些非同步的 API 呼叫，或者執行有延遲的含有 `setTimeout` 的程式碼，你可以在這個階段裡使用。

<br>

## 更新週期

`componentWillReceiveProps(object nextProps)`

這個元件的父元件傳來了新的 `props`。這個元件可能會重新顯示，你也可以視情況，在 `render` 辦法執行前，透過呼叫 `this.setState()` 以更新元件內部的狀態。

<br>

`shouldComponentUpdate(object nextProps, object nextState) -> boolean`

基於下一個 `props` 與 `state` 的值，元件可以決定是否要重新顯示。預設是會回傳 `true`(意味著會重新顯示)。為了優化，你可以覆寫這個辦法，檢查 `props` 或 `state` 是否有被修改。回傳 `false` 會阻止 `render` 辦法被執行。

<br>

`componentWillUpdate(object nextProps, object nextState)`

這個辦法會在決定要重新顯示之後被呼叫。你無法在這個階段裡呼叫 `this.setState()`，畢竟更新已經在進行當中了

<br>

`render() -> React Element`

假設 `shouldComponentUpdate` 回傳 `true`，這個辦法就會被呼叫。這個 render 辦法必須要回傳一個 React 物件以呈現些什麼 (null 的話就是什麼也不會呈現)

<br>

`componentDidUpdate(object prevProps, object prevState)`

這個辦法發生在畫面被重新生成之後。在這個階段裡，原生的 UI 已經被 `render()` 更新完畢。