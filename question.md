# 问答接口

##### 1、小程序登陆接口
url：/mina/login    
request：POST    

|参数|类型|参数说明|是否必须|备注|    
|--|--|--|--|--|    
|code|字符串|微信接口参数|是|微信接口参数|    
|aid|整型|公众号或小程序ID|是||    

response
```
{
  c: 0,  //[整形]状态码
  d: {
    sid: 'abc...',    // [字符串]用户session_id
    uid: 123,    // [整形]用户UID
  },
  msg: ''
}
```



##### 2、小程序基本用户信息上报接口
url：/mina/user_info_upload?sid={sid}    
request：POST    

|参数|类型|参数说明|是否必须|备注|
|--|--|--|--|--|
|encryptedData|字符串|加密数据|是|	
|iv|字符串|初始向量|是|

response
```
{
  c: 0,  //[整形]状态码
  d: {
    nickname: 'tlwlmy',    // [字符串]用户名
    headimgurl: 'http'   // [字符串]头像url
  }
  msg: ''
}
```


#### 3、查询题目列表
url：/question/lists    
request：GET    

|参数|类型|参数说明|是否必须|备注|
|--|--|--|--|--|
|sid|字符串|session_id|否|-|


response
```
{
  c: 0,  //[整形]状态码
  d: {
    sid: 'abc...',    // [字符串]用户session_id
    candidates: [    // [字符串]候选答案
      {
        mpoint: 0,    // [整形]大于等于此得分，答案为这个
        anwser: '',    // [字符串]答案
      },
      ...
    ],
    questions: [
      {
        qid: 123,    // [整形]问题ID
        name: '',    // [字符串]问题
        A: '',    // [字符串]选项A答案
        B: '',    // [字符串]选项B答案
        C: '',    // [字符串]选项C答案
        D: '',    // [字符串]选项D答案
        E: '',    // [字符串]选项E答案
      },
      ...
    ],
    qtotal: 10,    // [字符串]题目数
  }
  msg: ''
}
```

#### 4、题目回答上报
url：/question/answer_upload?sid={sid}
method：POST
request

|参数|类型|参数说明|是否必须|备注|
|--|--|--|--|--|
|answers|字符串|选项上报|是|json接口|

answer格式
```
{
 result: [
    {
      qid: 123,    // [整形]问题ID
      option: 'A',    // [字符串]问题选项
    },
    ...
 ],
}
```

response
```
{
  c: 0,  //[整形]状态码
  msg: ''
}
```
