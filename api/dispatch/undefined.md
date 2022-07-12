# 카카오톡 비즈메시지

### AT/AI**/FT**

![](<../../.gitbook/assets/image (24) (1) (1) (1) (1) (1).png>)

### BUTTON

![](<../../.gitbook/assets/image (3) (1).png>)

**버튼 타입 별 속성 (\*type)**

![](<../../.gitbook/assets/image (5) (1) (1).png>)

### ITEM

![](<../../.gitbook/assets/image (18) (1).png>)

### ITEMHIGHLIGHT

![](<../../.gitbook/assets/image (22) (1).png>)

### IMAGE

![](<../../.gitbook/assets/image (23) (1) (1) (1).png>)

### QUICKREPLY

![](<../../.gitbook/assets/image (15).png>)

**버튼 타입 별 속성 (\*type)**

![](<../../.gitbook/assets/image (26) (1) (1) (1).png>)

### Examples

**알림톡**

```json5
{
  "account": "test",
  "refkey": "test1234",
  "type": "at",
  "from": "07000000000",
  "to": "01000000000",
  "content": {
    "at": {
      "senderkey": "12345",
      "templatecode": "template",
      "message": "알림톡 + 버튼(WL)",
      "button": [
        {
          "name": "웹 링크 버튼",
          "type": "WL",
          "url_pc": "http://www.bizppurio.com",
          "url_mobile": "http://www.bizppurio.com"
        }
      ]
    }
  }
}
```



**알림톡 아이템 리스트형**

```json5
{
  "account": "test",
  "refkey": "test1234",
  "type": "at",
  "from": "07000000000",
  "to": "01000000000",
  "content": {
    "at": {
      "senderkey": "12345",
      "templatecode": "template",
      "message": "알림톡 아이템리스트 + 버튼(WL)",
      "header": "헤더 (최대 16자)",
      "button": [
        {
          "name": "웹 링크 버튼",
          "type": "WL",
          "url_pc": "http://www.bizppurio.com",
          "url_mobile": "http://www.bizppurio.com"
        }
      ],
      "item": {
        "list": [
          {
            "title": "타이틀",
            "description": "디스크립션"
          },
          {
            "title": "타이틀2",
            "description": "디스크립션2"
          }
        ],
        "summary": {
          "title": "요약 타이틀",
          "description": "$100,000원"
        }
      },
      "itemhighlight": {
        "title": "타이틀",
        "description": "디스크립션"
      }
    }
  }
}
```

**친구톡**

```json5
{
  "account": "test",
  "refkey": "test1234",
  "type": "ai",
  "from": "07000000000",
  "to": "01000000000",
  "content": {
    "ai": {
      "senderkey": "12345",
      "templatecode": "template",
      "message": "알림톡 이미지"
    }
  }
}
```
