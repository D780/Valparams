# 更新记录

## 3.13.2
>
> `array` 类型增加对 普通数组对象 和 `JSON` 数组对象 的兼容支持
>> 原本 `array` 是专指 `1,2,3` 这种用逗号分隔的字符串
>> 现在兼容直接传来 数组对象 或 `JSON` 数组对象，如 [1,2,3]、'["a","b",{"c":1}]'
>>>（此时其实是转换成了
>>> ```js
>>>   type = vType.JSON;
>>>   range = {
>>>     schema: {
>>>       type: 'array',
>>>     },
>>>   };
>>> ```
>>> 进行处理）
> 

## 3.13.1
>
> 修正参数间关系 `case` 条件判断的 `value` 处理 `bug`。（当 `value = false` 时判断处理有误）
> 

## 3.13.0
>
> `cookies` 增加 `signed` 的区分， 即分为 `cookies` 和 `signedCookies`
> 参数规则定义增加 `signed` 为 `cookies` 指定是否为已签名 `cookies`
> 特别地，`{ from: 'cookies', signed: true }` 等价于 `{ from: 'signedCookies' }`
> 

## 3.12.0
>
> 增加 `headers`、`cookies` 的验证  
> 调整各类参数获取优先级  
> 参数规则定义增加 `from` 指定来源
> 支持 `query`、`body` 等传相同键名参数（定义时 `key` 用不同的, 通过 `from` 指定来源及通过 `alias` 设置想同的别名）  
> 优化声明文件  
> 修正一处错误提示 `bug`  

## 3.11.0
>
> 增加对象形式参数支持（一般对象自动转换成 `json` 接收，`Date` 使用 `date）`

## 3.10.0
>
> 因为 `validator` 模块 `isNumeric` 方法调整，不再适用于判断是否为数字，更换该方法为使用 `isInt` || `isFloat` 判断

## 3.9.0
>
> [`lib/getparams`]  `3.7.1` -> `3.8.0`
> 参数配置增加 allowNull 的支持，开启时 传递 x=null 或 x='null' 时，可以跳过类型检查，将 null 值直接赋予 x 参数
> 此举可以在 POST PUT 之类的接口传入 null 参数把数据库记录的值设置为 null，或获取记录时候筛选 某值为 null 的记录

## 3.9.0
>
> [`lib/getparams`]  `3.7.1` -> `3.8.0`
> 参数配置增加 allowNull 的支持，开启时 传递 x=null 或 x='null' 时，可以跳过类型检查，将 null 值直接赋予 x 参数
> 此举可以在 POST PUT 之类的接口传入 null 参数把数据库记录的值设置为 null，或获取记录时候筛选 某值为 null 的记录

## 3.8.12
>
> 修正完善一些注释文档及更新 index.d.ts

## 3.8.10
>
> [`lib/getparams`]  `3.7.0` -> `3.7.1`
> [`lib/validators`] `3.2.0` -> `3.2.1`
> 修正完善一些注释文档，增加 `dts` 提供智能提示，便于使用

## 3.8.8
>
> 类型为 `JSON` 并且报错的时候，调整返回的错误信息，提供更详细的错误信息，比如具体到某个键的缺失等

## 3.8.5
>
> 增加 Array 数组类型的支持，可以识别 ,(英文逗号)分割的字符串数组 以及 post请求中直接传递的数组

## 3.8.4
>
> 增加 `Array` 数组类型的支持，可以识别 ,(英文逗号)分割的字符串数组 以及 `post` 请求中直接传递的数组

## 3.8.0
>
> [`lib/validators`] `3.1.0` -> `3.2.0`  增加 `min`、`max` 默认最大值

## 3.7.0
>
> [`lib/getparams`]  `3.6.0` -> `3.7.0`  增加参数关系限制 `cases`(条件控制) 支持定义 `when` `then` `not` 动态调整参数是否必填的情况

## 3.6.0
>
> [`lib/getparams`]  `3.5.0` -> `3.6.0`
> [`lib/validators`] `3.0.0` -> `3.1.0`
> 修正某些情况下中文的错误提示不正确
> 错误提示增加 `desc` 信息输出
> 增加参数 `allowEmptyStr`，是否允许空串变量 默认不允许， 即 `XXXX?YYY=` 这种路由 `YYY` 这个参数是否接受，默认这种情况认为没有传该参数

## 3.5.0
>
> 增加参数关系限制的支持
> [`lib/getparams`]  `3.4.0` -> `3.5.0` 现支持 `choices`（参数N选M） `equals`（参数值需相等） `compares`（参数值需为递增关系）

## 3.4.0
>
> 模块改用类的形式实现，增加国际化支持，目前可选 '`en`'、'`zh-cn`'，优化错误日志输出，增加对JSONSchema的支持（ajv）
> [`lib/locale`]  `0.0.0` -> `1.0.0`
> [`lib/locales`] `0.0.0` -> `1.0.0`
> [`lib/getparams`]  `3.3.0`  ->  `3.4.0`
> [`lib/validators`]  `2.1.0` -> `3.0.0`
> [`lib/type`]  `1.0.3` -> `1.0.4` 调整支持格式

## 3.3.0
>
> [`lib/getparams`]  `3.2.0` -> `3.3.0` 增加参数trim，是否要去除得到的值得首尾空格

## 3.2.0
>
> [`lib/getparams`]  `3.1.2` -> `3.2.0` 增加错误信息的检测返回
    调整规则 1 不管参数可选必选，除非有默认值，否则传了就应该符合我们设置的条件
            2 参数必选就必须传，默认值无效
> [`lib/validators`]  `2.0.3` -> `2.1.0` 增加错误信息的检测返回,修复 `IP` 大小判断时的转换错误问题

## 3.1.5
>
> [`FIXED`]  修复 `raw` 的 `query` 或者 `body` 没有得到没有传但是有默认值的参数

## 3.1.4
>
> [`lib/getparams`]  `3.1.1` -> `3.1.2` `value` 允许为 `null`, 取消不能为空串的限制,增加 `BOOL` 类型的转换
> [`lib/type`]  `1.0.2` -> `1.0.3` 增加 `phone` 和 `bool` 两种类型
> [`lib/validators`]  `2.0.2` -> `2.0.3` 增加 `phone` 和 `bool` 两种类型支持,修复仅设置 `min` 时, `isLength` 参数 `max` 的处理问题 `null` -> `undefined`

## 3.1.3
>
> [`lib/validators`]  `2.0.1` -> `2.0.2` `ip` 增加 `min` 和 `max` 的范围支持

## 3.1.2
>
> [`lib/getparams`]  `3.1.0` -> `3.1.1` `must` 参数换成使用 `required` ,目前保持支持用 `must`

## 3.1.1
>
> [`async`] `0.1.0` 提供 `promise` 版本
> [`sync`]  `3.0.0` 原版移到 sync 默认仍然是提供 sync
> [`lib/type`]  `1.0.0` -> `1.0.2` 增加 `range` `dateRange` `intRange` `floatRange` `numberRange`
> [`lib/getparams`]  `3.0.0` -> `3.1.0` 重构代码 增加 `XX>=[:]YY` 的参数支持如 `p6>=:5`  -> `p6={$gte:5}`

## 3.1.0
>
> [`ADDED`] `setParamsAsync`，提供 `promise` 版本的支持(`async`),原版不变
> 补全版本信息

## early
>
> 还没有 `changelog` 呢
