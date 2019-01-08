## 目录

* 1.通用约定


* 2.后台登录登出
>* 2.1登录
>* 2.2登出




* 3.故事梗概
>* 3.1 获取故事梗概
>* 3.2 创建故事梗概
>* 3.3 修改故事梗概


* 4.图片上传
>* 4.1 图片上传


* 5 章节介绍
>* 5.1 获取所有章节列表和内容
>* 5.2 创建新章节
>* 5.3 修改章节内容
>* 5.4 删除章节

* 6 人物介绍
>* 6.1 获取所有人物及其信息
>* 6.2 创建新人物
>* 6.3 修改人物信息
>* 6.4 删除人物

* 7 画廊
>* 7.1 获取所有图片
>* 7.2 添加新图片
>* 7.3 修改图片
>* 7.4 删除图片

* 8 最新消息
>* 8.1 获取所有最新消息
>* 8.2 新增最新消息
>* 8.3 修改最新消息
>* 8.4 删除最新消息

* 9 视频
>* 9.1 获取所有视频
>* 9.2 新增视频
>* 9.3 修改视频
>* 9.4 删除视频

* 10 获取底部信息
>* 11.1 获取底部信息
>* 11.2 新增底部信息
>* 11.3 修改底部信息

* 11 世界观
>* 11.1 获取所有世界观
>* 11.2 新增世界观
>* 11.3 修改世界观
 
* 12 SEO
>* 12.1 获取对应SEO
>* 12.2 新增SEO
>* 12.3 修改SEO
>* 12.4 删除SEO
 

* 13.Error Code

* * *

### 1.通用约定
* http://localhost 代表当前使用的环境域名
* 调用API（登录登出除外）都需要在header中传输Authentication，该值在登录成功后获取，有效时间2小时
* 统一回复格式
```angular2html
{
    "code": 0,
    "msg": "success",
    "data": {…}
}
```
> 返回值说明
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>code</td>
        <td>int</td>
        <td>API返回码，0为正常，更多返回码请查看Error Code</td>
        <td>0</td>
    </tr>
    <tr>
        <td>msg</td>
        <td>string</td>
        <td>错误信息，更多错误信息请查看Error Code</td>
        <td>0</td>
    </tr>
    <tr>
        <td>data</td>
        <td>Json</td>
        <td>请求返回的数据信息</td>
        <td>
          "data": {
          "access_token": "8enwxeL7WgYkldN1kxLCuN9VefThAgvo"}
        </td>
    </tr>
</table>

* * *


###  2 后台登录登出
#### 2.1 登录
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>登录</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/site/login</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>username</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>后台登录用户名</td>
        <td>admin</td>
    </tr>
    <tr>
        <td>password</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>后台登陆密码</td>
        <td>archisense2016</td>
    </tr>
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "success",
    "data": {
        "access_token": "8enwxeL7WgYkldN1kxLCuN9VefThAgvo"
       "username": "root"
    }
}
```
###### data参数说明
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>说明</td>
    </tr>
    <tr>
        <td>access_token</td>
        <td>string</td>
        <td>access_token用于API调用验证</td>
    </tr>
    <tr>
        <td>username</td>
        <td>string</td>
        <td>当前登录用户名</td>
    </tr>
</table>

#### 2.2登出
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>后台管理用户登出</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/site/logout</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
>无

###### 返回数据示例
```
{
    "code": 0,
    "msg": "success",
    "data": []
}
```
* * *




### 3.故事梗概

#### 3.1 获取故事梗概列表
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>获取故事梗概列表</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>GET</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/story/get-story</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
     <tr>
         <td>参数</td>
         <td>类型</td>
         <td>是否必传</td>
         <td>是否必填</td>
         <td>说明</td>
         <td>示例</td>
     </tr>
     <tr>
         <td>is_pc</td>
         <td>tinyint</td>
         <td>是</td>
         <td>是</td>
         <td>0 是pc ,1是mobile</td>
         <td>1</td>
     </tr>
 </table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": {
        "id": "3",
        "title": "故事梗概",
        "author": "火红森林",
        "theme": "的",
        "story_background": "但是",
        "introduction": "NEWS小说信息 故事梗概世界观介绍章节介绍人物介绍画廊\n故事讲述了作为普通大学毕业生的主人公姜爻在追查友人失踪案件中，意外得知自己本因在十年前就已死去的事实， 而自己也因“擅改天命”被地府烙下『死亡刻印』，遭到阎王的追捕。\n为了查清友人失踪的真相，也为了摆脱地府的追杀，身不由己的姜爻开始步步卷入人类与妖类的纷争之中，\n原本存在于古籍《山海经》中的魑魅魍魉们也在现代社会中悉数登场。在一次次穿梭于异界的冒险过程中，\n一场跨越千年的阴谋逐渐浮出水面……",
        "is_pc": "0",
        "create_time": "1544169684"
    }
}

```
###### data参数说明
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>说明</td>
    </tr>
    <tr>
        <td>id</td>
        <td>int</td>
        <td>后台消息数据id</td>
    </tr>
    <tr>
        <td>title</td>
        <td>string</td>
        <td>名字</td>
    </tr>
    <tr>
        <td>author</td>
        <td>string</td>
        <td>作者</td>
    </tr>
    <tr>
        <td>introduction</td>
        <td>string</td>
        <td>简介</td>
    </tr>
    <tr>
        <td>theme</td>
        <td>string</td>
        <td>题材</td>
    </tr>
    <tr>
        <td>story_background</td>
        <td>string</td>
        <td>故事背景</td>
    </tr>
    <tr>
        <td>create_time</td>
        <td>int</td>
        <td>创建时间</td>
    </tr>
    <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>0 是pc ,1是mobile</td>
    </tr>
</table>


#### 3.2 创建故事梗概
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>创建故事梗概</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/story/save-story</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
     <tr>
         <td>参数</td>
         <td>类型</td>
         <td>是否必传</td>
         <td>是否必填</td>
         <td>说明</td>
         <td>示例</td>
     </tr>
     <tr>
         <td>title</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>作品名</td>
         <td>作品名</td>
     </tr>
     <tr>
         <td>author</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>作者</td>
         <td>作者名称</td>
     </tr>
     <tr>
         <td>theme</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>题材</td>
         <td>题材</td>
     </tr>
     <tr>
         <td>story_background</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>故事背景</td>
         <td>故事背景</td>
     </tr>
     <tr>
         <td>introduction</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>简介</td>
         <td>故事介绍</td>
     </tr>
     <tr>
         <td>is_pc</td>
         <td>tinyint</td>
         <td>是</td>
         <td>是</td>
         <td>0 是pc ,1是mobile</td>
         <td>1</td>
     </tr>

 </table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
>无


#### 3.3 修改故事梗概

###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>修改故事梗概</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/story/edit-story</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
     <tr>
         <td>参数</td>
         <td>类型</td>
         <td>是否必传</td>
         <td>是否必填</td>
         <td>说明</td>
         <td>示例</td>
     </tr>
     <tr>
         <td>id</td>
         <td>int</td>
         <td>是</td>
         <td>是</td>
         <td>后台数据的ID</td>
         <td>1</td>
     </tr>
     <tr>
         <td>title</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>名称</td>
         <td>哎呀</td>
     </tr>
     <tr>
         <td>author</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>作者</td>
         <td>作者名称</td>
     </tr>
     <tr>
         <td>theme</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>题材</td>
         <td>题材</td>
     </tr>
     <tr>
         <td>story_background</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>故事背景</td>
         <td>故事背景</td>
     </tr>
     <tr>
         <td>introduction</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>简介</td>
         <td>故事介绍</td>
     </tr>
    <tr>
         <td>is_pc</td>
         <td>tinyint</td>
         <td>是</td>
         <td>是</td>
         <td>0 是pc ,1是mobile</td>
         <td>1</td>
    </tr>

 </table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
>无


* * *

###  4 图片上传
#### 4.1 图片上传
<table>
    <tr>
        <td>描述</td>
        <td>图片上传</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/site/upload-image</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>pic</td>
        <td>file</td>
        <td>是</td>
        <td>是</td>
        <td>图片文件</td>
        <td>pic</td>
    </tr>

</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": "/uploads/20181205/15439991681648.png"
}
```
###### data参数说明
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>说明</td>
    </tr>
    <tr>
        <td>data</td>
        <td>string</td>
        <td>图片路径</td>
    </tr>
</table>

* * *

###  5 章节介绍
#### 5.1 获取所有章节列表和内容
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>获取所有章节列表和内容</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>GET</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/chapter/get-chapter</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr>

</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": {
        "data": [
            {
                "id": "1",
                "title": "章节",
                "introduction": "阿萨德",
                "is_pc": "1",
                "create_time": "1544169684",
                "img_url":"/uploads/img/1.jpg"
            }
        ],
        "page_count": 1,
        "count": "1"
    }
}
```
###### data参数说明
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>说明</td>
    </tr>
    <tr>
        <td>id</td>
        <td>int</td>
        <td>章节id</td>
    </tr>
    <tr>
        <td>title</td>
        <td>string</td>
        <td>章节标题</td>
    </tr>
     <tr>
         <td>is_pc</td>
         <td>tinyint</td>
         <td>0是pc，1是mobile</td>
     </tr>
     <tr>
         <td>content</td>
         <td>string</td>
         <td>章节内容</td>
     </tr> 
     <tr>
         <td>create_time</td>
         <td>int</td>
         <td>创建时间</td>
     </tr> 
     <tr>
         <td>img_url</td>
         <td>json</td>
         <td>章节图片</td>
     </tr>
</table>

* * *

#### 5.2 创建新章节
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>创建新章节</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/chapter/save-chapter</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr> 
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>title</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>章节标题</td>
        <td>暗界神使</td>
    </tr>
    <tr>
        <td>content</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>章节内容</td>
        <td>暗界神使</td>
    </tr>
     <tr>
        <td>introduction</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>章节简介</td>
        <td>暗界神使</td>
    </tr>   
     <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr>
    <tr>
        <td>img_url</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
         <td>图片路径</td>
        <td>upload/img/1.jpg</td>
    </tr>         
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
无
* * *

#### 5.3 修改章节内容
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>修改章节内容</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/chapter/edit-chapter</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr> 
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr> 
    <tr>
        <td>id</td>
        <td>int</td>
        <td>是</td>
        <td>是</td>
        <td>1</td>
        <td>1</td>
        </tr>
    <tr>
        <td>title</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>章节标题</td>
        <td>暗界神使</td>
    </tr>
    <tr>
        <td>content</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>章节内容</td>
        <td>暗界神使</td>
    </tr>
     <tr>
        <td>introduction</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>章节简介</td>
        <td>暗界神使</td>
    </tr>   
     <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr>
    <tr>
        <td>img_url</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>图片路径</td>
        <td>/uploads/img/1.jpg</td>
    </tr>         
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
无
* * *

#### 5.4 删除章节
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>删除章节</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/chapter/del-chapter</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr> 
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr> 
    <tr>
        <td>id</td>
        <td>int</td>
        <td>是</td>
        <td>是</td>
        <td>1</td>
        <td>1</td>
        </tr>
    </table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
无
* * *

### 6. 人物介绍
##### 6.1 获取所有人物及其信息
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>获取所有人物及其信息</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>GET</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/user/get-characters</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr>

</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": {
        "data": [
            {
                "id": "1",
                "name": "姜爻",
                "cv": "边江",
                "gender": "1",
                "age": "23",
                "height": "178",
                "character": "低调、细心，性格偏内向，但重情义。",
                "identity": "毕业后找不到工作的无业青年，暗地里靠接黑客私活维持生活。",
                "ability": "拥有稀有体质“无色体质”，可以借用所有属性的法力，包括常人无法承受的[凶兽之力]。",
                "introduction": "<p>年少时因继父的关系家庭殷实，受过良好教育，但十年前遭遇变故而家道中落，并被迫背负上“杀死继父”的罪名，也因此无法通过正常途径找到工作。<p>",
                "small_picture": "/src/images/people/man_leader_pic.png",
                "big_picture": "/src/images/people/man_leader_pic.png",
                "is_pc": "1",
                "create_time": "1545725027"
            }
        ],
        "page_count": 1,
        "count": "1"
    }
}
```
###### data参数说明
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>说明</td>
    </tr>
    <tr>
        <td>id</td>
        <td>int</td>
        <td>人物id</td>
    </tr>
    <tr>
        <td>name</td>
        <td>string</td>
        <td>人物姓名</td>
    </tr>
     <tr>
         <td>cv</td>
         <td>string</td>
         <td>cv</td>
     </tr>
     <tr>
         <td>gender</td>
         <td>string</td>
         <td>性别 1=男2=女0=未知</td>
     </tr>
     <tr>
         <td>age</td>
         <td>int</td>
         <td>人物年龄</td>
     </tr>
     <tr>
         <td>height</td>
         <td>int</td>
         <td>身高</td>
     </tr>
     <tr>
         <td>character</td>
         <td>int</td>
         <td>性格</td>
     </tr>
     <tr>
         <td>identity</td>
         <td>string</td>
         <td>身份</td>
     </tr>
     <tr>
         <td>ability</td>
         <td>string</td>
         <td>人物能力</td>
     </tr>
     <tr>
         <td>introduction</td>
         <td>string</td>
         <td>人物介绍</td>
     </tr>
     <tr>
         <td>small_picture</td>
         <td>string</td>
         <td>小图</td>
     </tr>
     <tr>
         <td>big_picture</td>
         <td>string</td>
         <td>大图</td>
     </tr>
     <tr>
         <td>create_time</td>
         <td>int</td>
         <td>创建时间</td>
     </tr>
</table>

* * *

#### 6.2 创建新人物
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>创建新人物</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/user/save-character</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>  
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>name</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>人物姓名</td>
        <td>饕餮</td>
    </tr>
    <tr>
        <td>cv</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>cv</td>
        <td>男二</td>
    </tr>
     <tr>
        <td>character</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>人物性格</td>
        <td>狂妄</td>
    </tr>   
    <tr>
        <td>identity</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>人物身份</td>
        <td>反派</td>
    </tr>   
     <tr>
         <td>height</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>人物身高</td>
         <td>180</td>
     </tr>   
     <tr>
         <td>age</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>人物年龄</td>
         <td>20</td>
     </tr> 
     <tr>
         <td>ability</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>人物能力</td>
         <td>透视</td>
     </tr>
     <tr>
         <td>introduction</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>人物介绍</td>
         <td>xxxx</td>
     </tr>
     <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr>
    <tr>
        <td>small_picture</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>小图</td>
        <td>/uploads</td>
    </tr>
    <tr>
        <td>big_picture</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>大图</td>
        <td>/uploads</td>
    </tr>
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
无
* * *


#### 6.3 修改人物信息
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>修改人物信息</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/user/edit-character-introduction</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr> 
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr> 
    <tr>
        <td>id</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>人物id</td>
        <td>1</td>
   </tr>
    <tr>
        <td>name</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>人物姓名</td>
        <td>饕餮</td>
    </tr>
    <tr>
        <td>cv</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>cv</td>
        <td>男二</td>
    </tr>
     <tr>
        <td>character</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>人物性格</td>
        <td>狂妄</td>
    </tr>
    <tr>
        <td>identity</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>人物身份</td>
        <td>反派</td>
    </tr>
     <tr>
         <td>height</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>人物身高</td>
         <td>180</td>
     </tr>
     <tr>
         <td>age</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>人物年龄</td>
         <td>20</td>
     </tr>
     <tr>
         <td>ability</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>人物能力</td>
         <td>透视</td>
     </tr>
     <tr>
         <td>introduction</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>人物介绍</td>
         <td>xxxx</td>
     </tr>
     <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr>
    <tr>
        <td>small_picture</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>小图</td>
        <td>/uploads</td>
    </tr>
    <tr>
        <td>big_picture</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>大图</td>
        <td>/uploads</td>
    </tr>
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
无
* * *

#### 6.4 删除人物
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>删除人物</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/user/del-character-introduction</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr> 
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr> 
    <tr>
        <td>id</td>
        <td>int</td>
        <td>是</td>
        <td>是</td>
        <td>1</td>
        <td>1</td>
        </tr>
    </table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
无
* * *

### 7. 画廊
##### 7.1 获取所有图片
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>获取所有图片</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>GET</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/gallery/get-gallery</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr>
    <tr>
        <td>type</td>
        <td>int</td>
        <td>是</td>
        <td>是</td>
        <td>0是剧照,1是壁纸</td>
        <td>1</td>
    </tr>

</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": {
        "data": [
            {
                "id": "1",
                "title": "第一幕",
                "img_url": "/upload/img/1.jpg",
                "type": "1",
                "is_pc": "1",
                "create_time": "1545793423"
            }
        ],
        "page_count": 1,
        "count": "1"
    }
}
 ```
###### data参数说明
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>说明</td>
    </tr>
    <tr>
        <td>id</td>
        <td>int</td>
        <td>画廊id</td>
    </tr>
    <tr>
        <td>title</td>
        <td>string</td>
        <td>图片标题</td>
    </tr>
    <tr>
        <td>img_url</td>
        <td>string</td>
        <td>图片路径</td>
    </tr>
    <tr>
        <td>type</td>
        <td>int</td>
        <td>0是剧照,1是壁纸</td>
    </tr>
    <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>0是pc,1是mobile</td>
    </tr> 
    <tr>
        <td>create_time</td>
        <td>int</td>
        <td>创建时间</td>
    </tr> 
    
</table>

* * *

#### 7.2 添加新图片
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>添加新图片</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/gallery/save-gallery</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>  
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>type</td>
        <td>int</td>
        <td>是</td>
        <td>是</td>
        <td>画廊类别</td>
        <td>0是剧照,1是壁纸</td>
    </tr>
    <tr>
        <td>title</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>画廊标题</td>
        <td>第一幕</td>
    </tr>
    <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr>
    <tr>
        <td>img_url</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>图片路径</td>
        <td>upload/1.jpg</td>
    </tr>         
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
无
* * *

#### 7.3 修改图片
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>修改画廊</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/gallery/edit-gallery</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr> 
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr> 
    <tr>
        <td>id</td>
        <td>int</td>
        <td>是</td>
        <td>是</td>
        <td>画廊id</td>
        <td>1</td>
    </tr>
    <tr>
         <td>type</td>
         <td>int</td>
         <td>是</td>
         <td>是</td>
         <td>画廊类别</td>
         <td>0是剧照,1是壁纸</td>
    </tr>
    <tr>
         <td>title</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>画廊标题</td>
         <td>第一幕</td>
    </tr>
    <tr>
         <td>is_pc</td>
         <td>tinyint</td>
         <td>是</td>
         <td>是</td>
         <td>0是pc,1是mobile</td>
         <td>1</td>
    </tr>
    <tr>
         <td>img_url</td>
         <td>string</td>
         <td>是</td>
         <td>是</td>
         <td>图片路径</td>
         <td>upload/1.jpg</td>
    </tr>
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
无
* * *

#### 7.4 删除图片
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>删除图片</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/gallery/del-gallery</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr> 
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr> 
    <tr>
        <td>id</td>
        <td>int</td>
        <td>是</td>
        <td>是</td>
        <td>1</td>
        <td>1</td>
    </tr>
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
无
* * *

### 8. 最新消息
##### 8.1 获取所有最新消息
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>获取所有最新消息</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>GET</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/information/get-information</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr>
    
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": {
        "data": [
            {
                "id": "1",
                "title": "2018牛耳奖颁奖典礼落幕 《暗界神使》荣膺“互联网领域年度最具潜力文学”奖",
                "is_pc": "1",
                "img_url": "/upload/img/1.jpg",
                "content": "近日，被誉为“互联网奥斯卡”的2018年度牛耳奖颁奖典礼在北京演艺中心落下帷幕。创立于2010年的牛耳奖，作为中国新经济、新文化领域最具号召力与影响力的品牌奖项，备受行业关注。每一个奖项设置背后，都是牛耳奖对中国互联网行业新动态、投资新风向、行业大事件的高度洞察。",
                "create_time": "1545797053"
            }
        ],
        "page_count": 1,
        "count": "1"
    }
}
 ```
###### data参数说明
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>说明</td>
    </tr>
    <tr>
        <td>id</td>
        <td>int</td>
        <td>消息id</td>
    </tr>
    <tr>
        <td>title</td>
        <td>string</td>
        <td>情报标题</td>
    </tr>
    <tr>
        <td>content</td>
        <td>string</td>
        <td>情报内容</td>
    </tr>
    <tr>
        <td>img_url</td>
        <td>string</td>
        <td>缩略图</td>
    </tr>
    <tr>
       <td>is_pc</td>
       <td>tinyint</td>
       <td>0是pc,1是mobile</td>
    </tr>
    <tr>
      <td>create_time</td>
      <td>int</td>
      <td>创建时间</td>
    </tr>
</table>

* * *
#### 8.2 新增最新消息
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>新增最新消息</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/information/save-information</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>  
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>title</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>情报标题</td>
        <td>xxx</td>
    </tr>
    <tr>
        <td>content</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>情报内容</td>
        <td>xxx</td>
    </tr>
    <tr>
        <td>img_url</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>缩略图</td>
        <td>xxx</td>
    </tr>
    <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr>
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```

#### 8.3 修改最新消息
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>修改最新消息</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/information/edit-information</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr> 
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr> 
    <tr>
        <td>id</td>
        <td>int</td>
        <td>是</td>
        <td>是</td>
        <td>消息id</td>
        <td>1</td>
    </tr>
    <tr>
        <td>title</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>情报标题</td>
        <td>xxx</td>
    </tr>
    <tr>
        <td>content</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>情报内容</td>
        <td>xxx</td>
    </tr>
    <tr>
        <td>img_url</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>缩略图</td>
        <td>xxx</td>
    </tr>
    <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr>
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
####  8.4 删除最新消息
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>删除最新消息</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/information/del-information</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr> 
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr> 
    <tr>
        <td>id</td>
        <td>int</td>
        <td>是</td>
        <td>是</td>
        <td>1</td>
        <td>1</td>
        </tr>
    </table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
无
* * *

### 9. 视频
##### 9.1 获取所有视频
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>获取所有视频</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>GET</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/video/get-videos</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr>
      

</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": {
        "data": [
            {
                "id": "1",
                "title": "中日大作【暗界神使】动画先导PV公开！万代南梦宫出品 Sunrise协助",
                "video_url": "/src/images/people/1.mp4",
                "description": "大学毕业生姜爻在追查友人失踪案件中，意外得知自己本应在十年前就已死去的事实，而自己也因“擅改天命”被地府烙下『死亡刻印』，遭到阎王的追捕。\n为了查清友人失踪的真相，也为了摆脱地府的追杀，姜爻开始步步卷入人类与妖类的纷争之中，原本存在于古籍《山海经》中的魑魅魍魉们也将在现代社会中悉数",
                "produced": "万代南梦宫（上海）互动娱乐有限公司",
                "animation_contract": "海岸线动画",
                "production_assistance": "株式会社sunrise",
                "dubbing": "边江工作室",
                "cover": "/src/images/people/man_leader_pic.png",
                "is_pc": "1",
                "create_time": "1545728606"
            }
        ],
        "page_count": 1,
        "count": "1"
    }
}
 ```
###### data参数说明
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>说明</td>
    </tr>
    <tr>
        <td>id</td>
        <td>int</td>
        <td>视频id</td>
    </tr>
    <tr>
        <td>title</td>
        <td>string</td>
        <td>视频标题</td>
    </tr>
    <tr>
        <td>video_url</td>
        <td>string</td>
        <td>视频路径</td>
    </tr>
     <tr>
         <td>description</td>
         <td>string</td>
         <td>描述</td>
     </tr> 
      <tr>
        <td>produced</td>
        <td>string</td>
        <td>出品</td>
     </tr> 
      <tr>
        <td>animation_contract</td>
        <td>string</td>
        <td>动画承制</td>
     </tr>
     <tr>
        <td>production_assistance</td>
        <td>string</td>
        <td>制作协助</td>
     </tr>
     <tr>
        <td>dubbing</td>
        <td>string</td>
        <td>配音</td>
     </tr>
     <tr>
        <td>cover</td>
        <td>string</td>
        <td>封面</td>
     </tr>
     <tr>
      <td>is_pc</td>
      <td>tinyint</td>
      <td>0是pc,1是mobile</td>
     </tr> 
     <tr>
      <td>create_time</td>
      <td>int</td>
      <td>创建时间</td>
     </tr> 
    
</table>

* * *


#### 9.2 新增视频
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>新增视频</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/video/save-video</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>  
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>title</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>视频标题</td>
    </tr>
    <tr>
        <td>video_url</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>视频路径</td>
    </tr>
    <tr>
        <td>description</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>描述</td>
    </tr>
    <tr>
        <td>produced</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>出品</td>
    </tr>
    <tr>
        <td>animation_contract</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>动画承制</td>
    </tr>
    <tr>
        <td>production_assistance</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>制作协助</td>
    </tr>
    <tr>
        <td>dubbing</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>配音</td>
    </tr>
    <tr>
        <td>cover</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>封面</td>
    </tr>
    <tr>
       <td>is_pc</td>
       <td>tinyint</td>
       <td>是</td>
       <td>是</td>
       <td>0是pc,1是mobile</td>
    </tr>
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
无
* * *


#### 9.3 修改视频
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>修改视频</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/video/edit-video</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr> 
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr> 
    <table>
    <tr>  
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>id</td>
        <td>int</td>
        <td>是</td>
        <td>是</td>    
        <td>视频id</td>
        <td>1</td>
    </tr>
    <tr>
        <td>title</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>视频标题</td>
    </tr>
    <tr>
        <td>video_url</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>视频路径</td>
    </tr>
    <tr>
        <td>description</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>描述</td>
    </tr>
    <tr>
        <td>produced</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>出品</td>
    </tr>
    <tr>
        <td>animation_contract</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>动画承制</td>
    </tr>
    <tr>
        <td>production_assistance</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>制作协助</td>
    </tr>
    <tr>
        <td>dubbing</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>配音</td>
    </tr>
    <tr>
        <td>cover</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>封面</td>
    </tr>
    <tr>
       <td>is_pc</td>
       <td>tinyint</td>
       <td>是</td>
       <td>是</td>
       <td>0是pc,1是mobile</td>
    </tr>
</table>
        
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```

#### 9.4 删除视频
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>删除视频</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/video/del-video</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr> 
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr> 
    <tr>
        <td>id</td>
        <td>int</td>
        <td>是</td>
        <td>是</td>
        <td>1</td>
        <td>1</td>
        </tr>
    </table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
无
* * *


### 10. 底部
##### 10.1 获取底部信息
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>获取底部信息</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>GET</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/bottom/get-bottom-contents</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr>
    <tr>
        <td>type</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>1为公司详情,2为友情链接,3为微信,微博图片</td>
        <td>1</td>
    </tr>
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": {
        "data": [
            {
                "id": "3",
                "name": "电话",
                "content": "021-5231-9070",
                "is_pc": "0",
                "type": "1",
                "create_time": "1545722284"
            },
            {
                "id": "2",
                "name": "地址",
                "content": "上海市长宁区娄山关路523号金虹桥国际中心1座2606室",
                "is_pc": "0",
                "type": "1",
                "create_time": "1545722104"
            },
            {
                "id": "1",
                "name": "17K",
                "content": " http://www.17k.com/book/2744067.html",
                "is_pc": "0",
                "type": "2",
                "create_time": "1545722044"
            }
        ],
        "page_count": 1,
        "count": "3"
    }
}
 ```
###### data参数说明
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>说明</td>
    </tr>
    <tr>
        <td>id</td>
        <td>int</td>
        <td>后台id</td>
    </tr>
    <tr>
         <td>name</td>
         <td>string</td>
         <td>名称</td>
    </tr>
    <tr>
         <td>content</td>
         <td>tinyint</td>
         <td>内容</td>
    </tr>
    <tr>
         <td>is_pc</td>
         <td>tinyint</td>
         <td>0为pc,1为mobile</td>
    </tr>
    <tr>
         <td>type</td>
         <td>tinyint</td>
         <td>1为公司详情,2为友情链接,3为微信,微博图片</td>
    </tr>
    <tr>
         <td>create_time</td>
         <td>int</td>
         <td>创建时间</td>
    </tr>

</table>

* * *


#### 10.2 新增底部信息
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>新增底部信息</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/bottom/save-bottom-content</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
     <tr>
        <td>name</td>
        <td>string</td>
        <td>名称</td>
        <td>是</td>
        <td>是</td>
        <td>xxxx</td>
    </tr>
    <tr>
        <td>content</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>内容</td>
        <td>内容</td>
    </tr>
    <tr>
        <td>type</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>1为公司详情,2为友情链接,3为微信,微博图片</td>
        <td>1</td>
    </tr>
    <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr>
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
无
* * *

#### 11.3 修改底部信息
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>修改底部信息</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/world-view/edit-world-view</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
 <table>
        <tr>
            <td>参数</td>
            <td>类型</td>
            <td>是否必传</td>
            <td>是否必填</td>
            <td>说明</td>
            <td>示例</td>
        </tr>
        <tr>
            <td>id</td>
            <td>int</td>
            <td>是</td>
            <td>是</td>
            <td>视频id</td>
            <td>1</td>
        </tr>
     <tr>
        <td>name</td>
        <td>string</td>
        <td>名称</td>
        <td>是</td>
        <td>是</td>
        <td>xxxx</td>
    </tr>
    <tr>
        <td>content</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>内容</td>
        <td>内容</td>
    </tr>
    <tr>
        <td>type</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>1为公司详情,2为友情链接,3为微信,微博图片</td>
        <td>1</td>
    </tr>
    <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr>

</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```



* * *


### 11. 世界观
##### 11.1 获取所有世界观
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>获取所有世界观</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>GET</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/world-view/get-world-view</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr>
    
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": {
        "id": "1",
        "is_pc": "0",
        "introduction": "上古时期，以黄帝为首的人类与以蚩尤为首的妖类为了争取生存资源，开始了旷日持久的殊死战争，一时间生灵涂炭。 \n　　创造人类的天界之神『女娲』由于不忍看到人类覆灭，于是派了手下『羿』用三件『噬神之器』将妖类中的战斗主力——四大凶兽（饕餮、混沌、穷奇、梼杌）分别斩杀，大战局势由此逆转。 \n虽然最终这场上古大战以蚩尤身死，人类胜利告终，但人类担心蚩尤在轮回转世后重新发起战争，于是将蚩尤的三魂七魄拆分散尽，使他永世不得轮回。而女娲也因擅自干涉地界事物获罪，被迫陷入沉睡；『羿』也被天界驱逐，带着三神器不知所踪。　　 \n　　战后，人类与妖类达成了和解协议，妖将隐匿身份生活在人类社会中，不得伤人。为监督和平条款，妖类成立了联合政府组织『妖神府』，而人类则成立了对应组织『灵御台』，双方共同协作，并通过双方认可的执行人——『灵御神使』去处理那些在人类社会中与妖相关的各种纠纷。 \n　　千年以来，这两个隐藏于世的神秘组织一直持续运作着，直至人类步入现代社会后也依然如此，只是现代人对隐藏在身边的妖类浑然不觉。此次的故事便发生在现代社会之中。",
        "create_time": "1545709690"
    }
}
 ```
###### data参数说明
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>说明</td>
    </tr>
    <tr>
        <td>id</td>
        <td>int</td>
        <td>世界观id</td>
    </tr>
         <tr>
         <td>introduction</td>
         <td>string</td>
         <td>世界观内容</td>
    </tr>
     <tr>
          <td>is_pc</td>
          <td>tinyint</td>
          <td>0是pc,1是mobile</td>
     </tr> 
     <tr>
          <td>create_time</td>
          <td>int</td>
          <td>创建时间</td>
     </tr> 
    
</table>

* * *


#### 11.2 新增世界观
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>新增世界观</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/world-view/save-world-view</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>  
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
     <tr>
        <td>introduction</td>
        <td>string</td>
        <td>世界观介绍</td>
        <td>是</td>
        <td>是</td>       
        <td>xxxx</td>
    </tr>
    <tr>
        <td>is_pc</td>
        <td>tinyint</td>
        <td>是</td>
        <td>是</td>
        <td>0是pc,1是mobile</td>
        <td>1</td>
    </tr> 
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
无
* * *

#### 11.3 修改世界观
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>修改世界观</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/world-view/edit-world-view</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
 <table>
        <tr>  
            <td>参数</td>
            <td>类型</td>
            <td>是否必传</td>
            <td>是否必填</td>
            <td>说明</td>
            <td>示例</td>
        </tr>
        <tr>
            <td>id</td>
            <td>int</td>
            <td>是</td>
            <td>是</td>    
            <td>视频id</td>
            <td>1</td>
        </tr>
        <tr>
            <td>introduction</td>
            <td>string</td>
            <td>世界观介绍</td>
            <td>是</td>
            <td>是</td>       
            <td>xxxx</td>
        </tr>
        <tr>
            <td>is_pc</td>
            <td>tinyint</td>
            <td>是</td>
            <td>是</td>
            <td>0是pc,1是mobile</td>
            <td>1</td>
       </tr> 
        
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```



* * *

### 12. SEO
##### 12.1 获取所有SEO
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>获取所有SEO</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>GET</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/seo/get-seo</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>page_name</td>
        <td>int</td>
        <td>是</td>
        <td>是</td>
        <td>前端页面路由</td>
        <td>1</td>
    </tr>
    
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": {
        "data": [
            {
                "id": "1",
                "name": "姜爻",
                "title": "第一幕",
                "keywords": "姜爻",
                "description": "姜爻发威",
                "page_id": "1"
            }
        ],
        "page_count": 1,
        "count": "1"
    }
}
```
###### data参数说明
<table>
    <tr>
        <td>参数</td>
        <td>类型</td>
        <td>说明</td>
    </tr>
    <tr>
        <td>id</td>
        <td>int</td>
        <td>seoid</td>
    </tr>
    <tr>
         <td>name</td>
         <td>string</td>
         <td>页面名称</td>
    </tr>
    <tr>
          <td>title</td>
          <td>string</td>
          <td>seo标签</td>
    </tr> 
    <tr>
          <td>keywords</td>
          <td>string</td>
          <td>seo关键字</td>
     </tr>       
     <tr>
          <td>description</td>
          <td>string</td>
          <td>seo描述</td>
     </tr> 
     <tr>
          <td>page_name</td>
          <td>int</td>
          <td>前端路由名称</td>
     </tr> 
    
</table>

* * *


#### 11.2 新增seo
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>新增seo</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/seo/save-seo</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr>  
          <td>参数</td>
          <td>类型</td>
          <td>是否必传</td>
          <td>是否必填</td>
          <td>说明</td>
          <td>示例</td>
    </tr>
     <tr>
          <td>name</td>
          <td>string</td>
          <td>是</td>
          <td>是</td>
          <td>页面名称</td>
          <td>名称</td>
     </tr>
     <tr>
           <td>title</td>
           <td>string</td>
           <td>是</td>
           <td>是</td>
           <td>seo标签</td>
           <td>标签</td>
     </tr> 
     <tr>
           <td>keywords</td>
           <td>string</td>
           <td>是</td>
           <td>是</td>
           <td>seo关键字</td>
           <td>关键字</td>
      </tr>       
      <tr>
           <td>description</td>
           <td>string</td>
           <td>是</td>
           <td>是</td>
           <td>seo描述</td>
           <td>描述</td>
      </tr> 
      <tr>
           <td>page_id</td>
           <td>int</td>
           <td>是</td>
           <td>是</td>
           <td>前端路由名称</td>
           <td>1</td>
      </tr> 
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
无
* * *

#### 11.3 修改SEO
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>修改SEO</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/seo/edit-seo</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
 <table>
    <tr>  
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr>
    <tr>
        <td>id</td>
        <td>int</td>
        <td>是</td>
        <td>是</td>    
        <td>后台id</td>
        <td>1</td>
    </tr>
    <tr>
        <td>name</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>页面名称</td>
        <td>名称</td>
     </tr>
     <tr>
        <td>title</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>seo标签</td>
        <td>标签</td>
     </tr> 
     <tr>
        <td>keywords</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>seo关键字</td>
        <td>关键字</td>
      </tr>       
      <tr>
        <td>description</td>
        <td>string</td>
        <td>是</td>
        <td>是</td>
        <td>seo描述</td>
        <td>描述</td>
      </tr> 
      <tr>
        <td>page_name</td>
        <td>int</td>
        <td>是</td>
        <td>是</td>
        <td>前端路由名称</td>
        <td>1</td>
      </tr> 
        
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```


####11.4 删除SEO
###### 接口信息
 <table>
    <tr>
        <td>描述</td>
        <td>删除SEO</td>
    </tr>
    <tr>
        <td>协议</td>
        <td>Http</td>
    </tr>
    <tr>
        <td>请求方式</td>
        <td>POST</td>
    </tr>
    <tr>
        <td>请求地址</td>
        <td>http://localhost/admin/seo/del-seo</td>
    </tr>
    <tr>
        <td>数据返回格式</td>
        <td>Json</td>
    </tr>
</table>

###### 请求参数
<table>
    <tr> 
        <td>参数</td>
        <td>类型</td>
        <td>是否必传</td>
        <td>是否必填</td>
        <td>说明</td>
        <td>示例</td>
    </tr> 
    <tr>
        <td>id</td>
        <td>int</td>
        <td>是</td>
        <td>是</td>
        <td>1</td>
        <td>1</td>
        </tr>
</table>

###### 返回数据示例
```
{
    "code": 0,
    "msg": "Success",
    "data": []
}
```
###### data参数说明
无
* * *
























### 13.Error Code


<table>
    <tr>
        <td>返回码</td>
        <td>说明</td>
    </tr>
    <tr>
        <td>0</td>
        <td>Success</td>
    </tr>
    <tr>
        <td>40001</td>
        <td>Unknown Error</td>
    </tr>
    <tr>
        <td>40002</td>
        <td>Login Failure</td>
    </tr>
    <tr>
        <td>40003</td>
        <td>Permission Dend</td>
    </tr>
    <tr>
        <td>40004</td>
        <td>Missing Required Parameter '%PARAM%'</td>
    </tr>
    <tr>
        <td>40014</td>
        <td>Access token invalid or no longer valid</td>
    </tr>
    <tr>
        <td>40015</td>
        <td>Access token expired</td>
    </tr>
    <tr>
        <td>40016</td>
        <td>No User Data</td>
    </tr>
    <tr>
        <td>40017</td>
        <td>No Code Data</td>
    </tr>
    <tr>
        <td>40018</td>
        <td>QR Code Repetition</td>
    </tr>
    <tr>
        <td>40019</td>
        <td>QR Code Generation Failed</td>
    </tr>
    <tr>
        <td>40020</td>
        <td>No Tag Data</td>
    </tr>
    <tr>
        <td>40021</td>
        <td>Tag Is Used For Other QR Code</td>
    </tr>
    <tr>
        <td>40022</td>
        <td>No Menu Data</td>
    </tr>
    <tr>
        <td>40023</td>
        <td>No Data Delete</td>
    </tr>
    <tr>
        <td>40024</td>
        <td>Empty Order Delete</td>
    </tr>
    <tr>
        <td>40025</td>
        <td>No Keyword Data</td>
    </tr>
</table>

