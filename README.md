# tp_py_flask

flask项目模版.

python构造服务在性能方面不占优势,唯一可以想到的原因有如下:

1. 希望使用其计算库,python是多数计算库的接口语言,比如pytorch,pandas等这是别的语言没有的优势.
2. 对并发性能要求不高,但要求快速开发快读迭代.这种需求一般用在工具型应用上,用啥不重要因为用户基本不会太多(最多万级),且对体验有一定容忍度.很少有像python这样可以半天弄出个能跑的服务的编程语言.

flask是python环境下最成熟的同步语法微框架之一,由于它使用同步语法因此对python下的计算库支持很好,是最经济适用的python网络框架.

## 项目组织形式

本项目是flask项目的模板,使用分支管理组件和模版的开发,tag固定版本,

+ dev分支:维护最新的的组件,组件tag全部从这里分出,统一使用cp-0.0.0作为前缀
+ master分支用于测试各种模版配置,模版tag全部从这里分出,统一使用api-0.0.0这样的形式,前缀分为:

    + `static`,静态资源服务模板
    + `rest`,RESTfulapi服务模版
    + `ws`,websocket服务模版
    + `api`,包含RESTful接口,sse接口,和websocket接口的服务模版
    + `spa`,混合api,ws,sse和download的单页应用模版.
    + `mvc`,由jinja2模版动态渲染的应用模版
    + `mvcapi`,由jinja2模版动态渲染的应用模版同时包含RESTful接口,sse接口,和websocket接口的服务模版

## 用法说明

使用模版构造项目后可以进行如下进一步操作:

+ 增加调试用的客户端组件

    + `ppm project add cp_py_files@v0.0.2//aiossecli --located-path=aiossecli.py` 异步sse客户端
    + `ppm project add cp_py_files@v0.0.2//ssecli --located-path=ssecli.py` 同步sse客户端
    + `ppm project add cp_py_files@v0.0.2//aiowscli --located-path=aiowscli.py` 异步websocket客户端
    + `ppm project add cp_py_files@v0.0.2//wscli --located-path=wscli.py` 同步websocket客户端

+ 增加功能组件中的资源项

    + `ppm project add tp_py_flask@cp-0.0.1//api_source --located-path=testflask/api/usernamespace --kv=source::user`增加一个api资源
    + `ppm project add tp_py_flask@cp-0.0.1//ws_source --located-path=testflask/ws/usernamespace.py --kv=source::user`增加一个websocket资源
    + `ppm project add tp_py_flask@cp-0.0.1//sse_source --located-path=testflask/sse/usernamespace.py --kv=source::user`增加一个sse资源
