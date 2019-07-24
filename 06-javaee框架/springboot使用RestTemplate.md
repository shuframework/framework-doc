

# RestTemplate报错：no suitable HttpMessageConverter found for request type

<https://blog.csdn.net/qq_23888451/article/details/84637956>

原因是返回 json的时候 response的返回头中content-type 不是 application/json;charset=utf-8