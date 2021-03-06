# **TIME 컴포넌트** 

## 개요
* `TIME` 컴포넌트는 시간을 입력하는 UI 컴포넌트입니다. `TIME` 컴포넌트를 사용하면 사용자가 키보드를 사용하지 않고 간편하게 시간을 입력할 수 있으며, 챗봇에게는 시간 데이터가 일정한 형식으로 전달되므로 처리가 수월해집니다.
* 아래 이벤트 명세는 [`button`](/README.md#button-object) 요소에서의 컴포넌트 작성 방법을 설명 합니다. `button`이 사용 가능한 위치는 [UI 컴포넌트](/ui_component_v1.md)를 참고해주세요. 

## 이벤트 명세서
```javascript
{
    "type": "TIME",
    "data": {
        "title": "타이틀",
        "code": "코드"
    }
}
```

| key | Type | 필수 | 설명 |
|:---:|:----:|:----:|------|
| `type` | string | Y | `TIME` 고정값 |
| `title` | string | N | 버튼과 컴포넌트 타이틀에 노출되는 텍스트, 기본값 '시간 선택하기'|
| `code` | string | N | 컴포넌트의 확인 버튼 클릭시 챗봇에게 전송되는 코드 |

> **[주의사항]**
> * `title`의 최대 길이는 18자 입니다.
> * `code`의 최대 길이는 1,000자 입니다.
<br>

#### `textContent -> quickReply -> buttonList[] -> button`에 적용한 예시
```javascript
{
  "event": "send",
  "user": "al-2eGuGr5WQOnco1_V-FQ",
  "textContent": {
    "text": "방문 시간을 선택해 주세요.",
    "quickReply": {
      "buttonList": [
        {
          "type": "TIME",
          "data": {
            "title": "방문 시간 선택",
            "code": "code_for_your_bot"
          }
        }
      ]
    }
  }
}
```
 * 위 이벤트 전송시 사용자 화면
 
![image](/images/time-component-chat.PNG)

 * button 클릭시 열리는 view
 
[Mobile - webview]

![image](/images/time-component-mobile.PNG)

[PC - popup]

![image](/images/time-component-pc.png)

 * 컴포넌트에서 확인 클릭시
   * 사용자 화면에는 `오후 2:00` 텍스트가 노출됩니다.
   * 챗봇에 전송 되는 데이터는 아래와 같습니다.
 ```javascript
 {
  "event": "send",
  "user": "al-2eGuGr5WQOnco1_V-FQ",
  "textContent": {
    "text": "14:00",
    "code": "code_for_your_bot",
    "inputType": "time"
  }
}
```
<br>
