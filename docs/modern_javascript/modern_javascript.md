# 現代的 javascript

作者：[@dvnabbott](https://twitter.com/dvnabbott)  
譯者：朱文藝

以前，你只要在網頁的開頭加入 `<script>` 標籤即可使用 JavaScript。而如今，我們需要事先處理 JavaScript 以能夠使用實驗性前端的功能以及如 JSX 的延伸語言。

## Babel

Babel 是事先處理 JavaScript 的主要工具。Babel 編譯器的功能很強大，可以讓你使用實驗性前端的功能以及延伸套件，它的輸出結果可以向下相容 JavaScript 舊語法，於是可以在很多平台上運行。

當然，如果原本的平台便不支援 ES6 裡的功能，比如 `Promise()`，Babel 就也幫不上忙 — 但是在很多情況下它可以補足缺漏的 API 以提供對應的功能。

Babel 藉由在編譯好的 JavaScript 裡放入 **sourec maps** 以協助你除錯。JavaScript 的直譯器將會執行編譯好的程式碼，並且在 debugger 裡
對回原始程式碼，這樣你就不用在除蟲時面對通常非常醜陋的輸出畫面。

## Babel 設定

你可以在專案的根目錄底下的 `.babelrc` 裡設定 Babel。這個檔案可以特別使用來指名那些實驗性的 JS 功能以及套件將會啟用(JSX)。

React Native 會自動為你照料 babel 的設定，所以通常你不需要建立 `.babelrc` 檔案。然而，如果你想要更改預設的內容，你可以使用 npm 套件 [babel-preset-react-native](https://github.com/facebook/react-native/tree/master/babel-preset) 為基底，並在上頭套用額外的套件或設定值。