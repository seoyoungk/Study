# WKWebView에서 외부 링크가 안 열릴 때

자바스크립트의 window.open()의 역할로, 
WebView상에서 자동적으로 window.open()을 처리할 수 있는게 아니기 때문에 WebView 내에서 원활하게 작동할 수 있도록 설계를 해줘야 한다.

```swift
webView.uiDelegate = self
webView.navigationDelegate = self

func webView(_ webView: WKWebView, createWebViewWith configuration: WKWebViewConfiguration, for navigationAction: WKNavigationAction, windowFeatures: WKWindowFeatures) -> WKWebView? {
	if navigationAction.targetFrame == nil {
		webView.load(navigationAction.request)
	}
	return nil
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTkyNDI1MzU5OV19
-->