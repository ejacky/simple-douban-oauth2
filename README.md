simple-douban-oauth2
====================

A simple douban oauth2 example

###Simple Douban Oauth使用方法

在example文件中演示了一个使用POST方法添加书评的例子。

    https://github.com/zither/simple-douban-oauth2/blob/master/example.php

**NOTICE:**需要注意到是例子中的代码只为演示，因此没有做任何过滤和有效性检查。

###添加API方法

无需授权API的GET请求样式为：

    public function userGet($id)
    {
        $this->uri = '/v2/user/'.$id;

        return $this;
    }

需要授权API的GET请求样式为：

    public function userMe($accessToken)
    {
        $this->uri = '/v2/user/~me';

        // 必须在header中发送授权令牌
        $this->header = array('Authorization: Bearer '.$accessToken);

        return $this;
    }

API的POST请求样式为：

    public function reviewAdd($accessToken)
    {
        $this->uri = "/v2/book/reviews";

        $this->header = array(
                'Content_type: application/x-www-form-urlencoded',
                'Authorization: Bearer '.$accessToken
                );

        // API默认请求设置为GET，因此这里需说明请求类型
        $this->type = 'POST';

        return $this;     
        }

了解API样式之后就可以把自己需要的豆瓣API添加到**DoubanAPI**文件中了。
