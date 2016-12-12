---
title: opm_api文档
kind: opm
tags:
---


### OPM-API文档

#### RBAC API

##### 系统登录
    地址: /api/login

    方法: post
    
    登录json
    {“user”:”xxxx”,”pwd”:”md5加密”}

    返回json
    {"status": "SUCCESS", "result": {"code": 200, "mes": "\u9a8c\u8bc1\u901a\u8fc7",
     "token": "33EF3C7EB15611E68E8D52540044ED7E"}
    }

    说明:
    - 登陆验证成功后会返回一个token值，作为会话的唯一索引，后面的任何前端操作请求都会验证token
    - 第一次登陆后会返回前端UI资源的该用户具有的顶部子系统的code和第一个子系统的左侧菜单code列表

    测试:
    curl -H "Content-type: application/json" -X POST -d 'user=zhangjiehz&pwd=123456' 'http://127.0.0.1:10001/login'

##### 初始化菜单
    地址: /api/init_menu
    
    方法: post
    
    登录json
    {"token":"xxxx"}

    返回json
    {
        "status": "SUCCESS",
        "result":
        {
            "token": "xxxx",
            "code": 1200,
            "menus":
            {
                "topmenu_codes":
                [
                    "t_1",
                    "t_2",
                    "t_3",
                    "t_4"
                ],
                "leftmenu_codes":
                [
                    "l_t2_2",
                    "l_t2_1",
                    "l_t2_1_1",
                    "l_t2_1_2",
                    "l_t2_1_3",
                    "l_t2_1_4",
                    "l_t2_1_5",
                    "l_t2_1_6",
                    "l_t2_1_7",
                    "l_t2_2_1",
                    "l_t2_2_2",
                    "l_t2_2_3",
                    "l_t2_2_4",
                    "l_t2_2_5"
                ],
                "menus":
                [
                    {
                        "icon": null,
                        "class": null,
                        "order": 1,
                        "parent_id": 0,
                        "name": "RBAC权限管理中心",
                        "children":
                        [
                        ],
                        "code": "t_1",
                        "id": 1,
                        "url": ""
                    },
                    {
                        "icon": "",
                        "class": "",
                        "order": 2,
                        "parent_id": 0,
                        "name": "CMDB配置管理中心",
                        "children":
                        [
                            {
                                "icon": null,
                                "class": null,
                                "order": 1,
                                "parent_id": 2,
                                "name": "业务资源",
                                "children":
                                [
                                    {
                                        "icon": null,
                                        "class": null,
                                        "order": 1,
                                        "parent_id": 5,
                                        "name": "部门",
                                        "children":
                                        [
                                        ],
                                        "code": "l_t2_2_1",
                                        "id": 17,
                                        "url": "#"
                                    },
                                    {
                                        "icon": null,
                                        "class": null,
                                        "order": 2,
                                        "parent_id": 5,
                                        "name": "产品",
                                        "children":
                                        [
                                        ],
                                        "code": "l_t2_2_2",
                                        "id": 18,
                                        "url": "#"
                                    },
                                    {
                                        "icon": null,
                                        "class": null,
                                        "order": 3,
                                        "parent_id": 5,
                                        "name": "子产品",
                                        "children":
                                        [
                                        ],
                                        "code": "l_t2_2_3",
                                        "id": 19,
                                        "url": "#"
                                    },
                                    {
                                        "icon": null,
                                        "class": null,
                                        "order": 4,
                                        "parent_id": 5,
                                        "name": "供应商",
                                        "children":
                                        [
                                        ],
                                        "code": "l_t2_2_4",
                                        "id": 20,
                                        "url": "#"
                                    },
                                    {
                                        "icon": null,
                                        "class": null,
                                        "order": 5,
                                        "parent_id": 5,
                                        "name": "部署实例",
                                        "children":
                                        [
                                        ],
                                        "code": "l_t2_2_5",
                                        "id": 21,
                                        "url": "#"
                                    }
                                ],
                                "code": "l_t2_2",
                                "id": 5,
                                "url": "#"
                            },
                            {
                                "icon": null,
                                "class": null,
                                "order": 2,
                                "parent_id": 2,
                                "name": "基础资源",
                                "children":
                                [
                                    {
                                        "icon": null,
                                        "class": null,
                                        "order": 1,
                                        "parent_id": 6,
                                        "name": "公网IP",
                                        "children":
                                        [
                                        ],
                                        "code": "l_t2_1_1",
                                        "id": 10,
                                        "url": "#"
                                    },
                                    {
                                        "icon": null,
                                        "class": null,
                                        "order": 2,
                                        "parent_id": 6,
                                        "name": "内网IP",
                                        "children":
                                        [
                                        ],
                                        "code": "l_t2_1_2",
                                        "id": 11,
                                        "url": "#"
                                    },
                                    {
                                        "icon": null,
                                        "class": null,
                                        "order": 3,
                                        "parent_id": 6,
                                        "name": "金属裸机",
                                        "children":
                                        [
                                        ],
                                        "code": "l_t2_1_3",
                                        "id": 12,
                                        "url": "#"
                                    },
                                    {
                                        "icon": null,
                                        "class": null,
                                        "order": 4,
                                        "parent_id": 6,
                                        "name": "虚拟机",
                                        "children":
                                        [
                                        ],
                                        "code": "l_t2_1_4",
                                        "id": 13,
                                        "url": "#"
                                    },
                                    {
                                        "icon": null,
                                        "class": null,
                                        "order": 5,
                                        "parent_id": 6,
                                        "name": "数据中心",
                                        "children":
                                        [
                                        ],
                                        "code": "l_t2_1_5",
                                        "id": 14,
                                        "url": "#"
                                    },
                                    {
                                        "icon": null,
                                        "class": null,
                                        "order": 6,
                                        "parent_id": 6,
                                        "name": "机柜",
                                        "children":
                                        [
                                        ],
                                        "code": "l_t2_1_6",
                                        "id": 15,
                                        "url": "#"
                                    },
                                    {
                                        "icon": null,
                                        "class": null,
                                        "order": 7,
                                        "parent_id": 6,
                                        "name": "交换机",
                                        "children":
                                        [
                                        ],
                                        "code": "l_t2_1_7",
                                        "id": 16,
                                        "url": "#"
                                    }
                                ],
                                "code": "l_t2_1",
                                "id": 6,
                                "url": "#"
                            }
                        ],
                        "code": "t_2",
                        "id": 2,
                        "url": "cmdb.ywdy1"
                    },
                    {
                        "icon": "",
                        "class": "",
                        "order": 3,
                        "parent_id": 0,
                        "name": "混合云管理中心",
                        "children":
                        [
                        ],
                        "code": "t_3",
                        "id": 3,
                        "url": "hhy.hhy1-1"
                    },
                    {
                        "icon": "",
                        "class": "",
                        "order": 4,
                        "parent_id": 0,
                        "name": "远程操作管理中心",
                        "children":
                        [
                        ],
                        "code": "t_4",
                        "id": 4,
                        "url": "yccz.yccz1-1"
                    }
                ]
            }
        }
    }
    说明:
    - 返回该用户具有的菜单资源

    测试:
    curl -H "Content-type: application/json" -X POST -d 'token=XXXXXXXXXXXXXXXXXXXXXXXXX' 'http://127.0.0.1:10001/init_menu'    


##### 注销当前用户
    地址: /api/logout
    
    方法: post
    
    登录json
    {"token":"xxxx"}

    返回json
    {"status": "SUCCESS", "result": {"code": 200,"mes": "注销成功!"}}
    如果客户端没发送token返回:
    {"status": "SUCCESS", "result": {"code": 401, "mes": "token missing"}}

    说明:
    - 注销用户，安全退出，后端注销会话

    测试:
    curl -H "Content-type: application/json" -X POST -d 'token=XXXXXXXXXXXXXXXXXXXXXXXXX' 'http://127.0.0.1:10001/logout'

##### 返回当前用户的会话信息
    地址: /api/session
    
    方法: post
    
    登录json
    {"token":"xxxx"}

    返回json
    {"status": "SUCCESS", "result": {"phone1": "13588888888", "email":"yyyyyy@ss.com","rolename":"系统管理员","mes": ""}}

    说明:
    - 会话信息包括用户的个人信息，如手机、电话、等

    测试:

#### CMDB API

##### 获取CI配置项元信息
    地址: /api/<ci>/schema

    方法: get

    返回json:
    {
        "result":
        {
            "fields":  # 字典名
            [
                "name",
                "cores",
                "ram",
                "hdd",
                "os",
                "inner_ip",
                "pwd",
                "use",
                "contact",
                "assigned_date",
                "status",
                "remarks"
            ],
            "schema":
            [
                {
                    "name": "虚拟机名",
                    "required": 1,
                    "show": 1,
                    "field": "name",
                    "type": "STRING",
                    "readonly": 1,
                    "type_value": "",
                    "uniqueness": 1
                },
                {
                    "name": "核数",
                    "required": 1,
                    "show": 1,
                    "field": "cores",
                    "type": "INT",
                    "readonly": 0,
                    "type_value": "",
                    "uniqueness": 0
                },
                {
                    "name": "内存",
                    "required": 1,
                    "show": 1,
                    "field": "ram",
                    "type": "INT",
                    "readonly": 0,
                    "type_value": "",
                    "uniqueness": 0
                },
                {
                    "name": "磁盘容量",
                    "required": 1,
                    "show": 1,
                    "field": "hdd",
                    "type": "INT",
                    "readonly": 0,
                    "type_value": "",
                    "uniqueness": 0
                },
                {
                    "name": "操作系统",
                    "required": 1,
                    "show": 1,
                    "field": "os",
                    "type": "STRING",
                    "readonly": 0,
                    "type_value": "",
                    "uniqueness": 0
                },
                {
                    "name": "内网IP",
                    "required": 1,
                    "show": 1,
                    "field": "inner_ip",
                    "type": "STRING",
                    "readonly": 0,
                    "type_value": "",
                    "uniqueness": 0
                },
                {
                    "name": "密码",
                    "required": 1,
                    "show": 1,
                    "field": "pwd",
                    "type": "STRING",
                    "readonly": 0,
                    "type_value": "",
                    "uniqueness": 0
                },
                {
                    "name": "用途",
                    "required": 0,
                    "show": 0,
                    "field": "use",
                    "type": "STRING",
                    "readonly": 0,
                    "type_value": "",
                    "uniqueness": 0
                },
                {
                    "name": "联系人",
                    "required": 0,
                    "show": 1,
                    "field": "contact",
                    "type": "STRING",
                    "readonly": 0,
                    "type_value": "",
                    "uniqueness": 0
                },
                {
                    "name": "分配时间",
                    "required": 0,
                    "show": 0,
                    "field": "assigned_date",
                    "type": "DATETIME",
                    "readonly": 0,
                    "type_value": "",
                    "uniqueness": 0
                },
                {
                    "name": "状态",
                    "required": 0,
                    "show": 0,
                    "field": "status",
                    "type": "ENUM",
                    "readonly": 0,
                    "type_value": "['启用','停用']",  # 前端以下拉列表的方式展现
                    "uniqueness": 0
                },
                {
                    "name": "备注",
                    "required": 0,
                    "show": 0,
                    "field": "remarks",
                    "type": "STRING",
                    "readonly": 0,
                    "type_value": "",
                    "uniqueness": 0
                }
            ]
        },
        "status": "SUCCESS"
    }

    说明: 后去CI配置项的元信息，字段，类型，约束等
    name: 字段中文名
    required: 是否为必填项
    readonly: 是否只读
    uniqueness: 是否为该实体的唯一值，一个实体的位置字段可能是几个字段合起来为唯一标示
    show: 前端列表是否展现
    type: 类型
    type_value: 如果是枚举类型，该处为枚举值

    测试:
    curl http://127.0.0.1:10001/vm/schema


##### 新增配置项
    地址: /api/<ci>/add

    方法: post

    发送json

    返回json

    说明:

    测试:


##### 删除配置项
    地址: /api/<ci>/del

    方法: delete

    发送json

    返回json

    说明:

    测试:

##### 删除配置项实例
    地址: /api/<ci>/del/<objid>

    方法: delete

    发送json

    返回json

    说明:

    测试:



##### 更新配置属性(非只读)
    地址: /api/<ci>/update

    方法: put

    发送json

    返回json

    说明:

    测试:

