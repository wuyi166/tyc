## `简介`

`IDDC 企业信息查询支持：`

*   [企业基本信息](#企业基本信息查询返回的数据)
*   [企业变更记录](#企业变更记录查询返回的数据)
*   [企业股东信息](#企业股东信息查询返回的数据)
*   [企业主要人员](#企业主要人员查询返回的数据)
*   [企业分支机构](#企业分支机构查询返回的数据)
*   [企业法律诉讼](#企业法律诉讼查询返回的数据)
*   [企业被执行人](#企业被执行人查询返回的数据)
*   [企业失信人](#企业失信人查询返回的数据)
*   [企业经营异常](#企业经营异常查询返回的数据)
*   [企业行政处罚](#企业行政处罚查询返回的数据)
*   [企业严重违法](#企业严重违法查询返回的数据)
*   [企业搜索](#企业搜索查询返回的数据)

 

### 调用查询方式
#### 调用说明

**URL** 为对应的服务器域名地址

```
http://URL/enterpinfo/v1/api?companyName=平安银行股份有限公司&type=114&apiKey=D7D93E04FXXXXXX98E94XXXXX5A8AF33933195C434&secretKey=191446631XXXXXXXXXX33E3E455D51A4884230632692B9CCC1A7DB0B2F0770815D772097CF7619A88C
```

#### 参数说明

| 属性        | 说明                            |
| ----------- | ------------------------------- |
| companyName | 查询企业的名字                  |
| type        | 查询[业务类型](#业务类型映射表) |
| apiKey      | 授权码                          |
| secretKey   | 授权验证码                      |

#### 业务类型映射表
| 值   | 说明         |
| ---- | ------------ |
| 110  | 企业基本信息 |
| 111  | 企业分支机构 |
| 112  | 企业变更记录 |
| 113  | 企业股东信息 |
| 114  | 企业主要人员 |
| 130  | 企业失信人 |
| 131  | 企业被执行人 |
| 132  | 企业法律诉讼 |
| 133  | 企业严重违法 |
| 140  | 企业经营异常 |
| 140  | 企业图谱 |
| 109  | 企业搜索 |



#### 返回JSON对象：
| 属性    | 说明                                   |
| ------- | -------------------------------------- |
| success | ture 标识与服务器通信正常              |
| code    | 200 服务器内部运行正常接受本次请求     |
| msg     | 服务器返回的信息，失败的情况有详细信息 |
| data    | 返回查询的数据【参见data数据对象】     |
| extra    | 不用，服务器返回的额外信息     |

`返回列子如下：

```
{
	"success": true,
	"code": 200,
	"msg": "service is ok",
	"data": {
	 	查询的数据主体[data](#data数据格式)
	},
	"extra": null
}
```

重点关注code 返回值为200，非200值请关注msg参数返回的信息。

当code 为200返回值，并不代表data就一定返回数据。

#### data数据格式

返回结构如下：
```
{
	"result": {	
	 返回的查询数据体	 
	},
	"reason": "ok",
	"error_code": 0
}
```
**返回值说明**
| 属性    | 说明                                   |
| ------- | -------------------------------------- |
| error_code | 0 请求成功  其他请参 error_code 错误码          |
| reason   | 服务器返回的信息    |
| result     | 返回的查询数据信息主体 |

**error_code 错误代码**

| 代码    | 说明 |
| ------- |  -------------------------------------- |
| 0	| 请求成功|
| 300000	| 无数据|
| 300001	| 请求失败|
| 300005	| 无权限访问此api|
| 300011	| 此IP无权限访问此api|


## 业务返回数据结构主体
### 企业基本信息查询返回的数据

![](https://iddc2.deloitte.com.cn/asset/images/baseinfo.jpg)

**result 返回数据示例**

```
 {
  "error_code": 0,
  "reason": "ok",
  "result(entityType=1)": {
        "updatetime":1551156181658,
        "phoneList":[
            "67594008",
            "67591191",
            "023-67591191"
        ],      
        "fromTime":846691200000,
        "type":1,
        "entityType":1,
        "emailList":[
            "cazqc@changan.com.cn",
            "hr@changan.com.cn"
        ],
        "usedBondName":"长安汽车->G长安",
        "isHightTech":"1",
        "percentileScore":9987,
        "haveReport":true,
        "phoneNumber":"67594008",
        "regInstitute":"重庆市市场监督管理局",
        "regLocation":"重庆市江北区建新东路260号",
        "industry":"汽车制造业",
        "businessScope":"制造、销售汽车（含轿车），制造汽车发动机系列产品。 汽车（含小轿车）开发，汽车发动机系列产品的开发、销售，配套零部件、模具、工具的、开发，制造，销售，机械安装工程科技技术咨询服务，自营和代理各类商品和技术的进出口（国家限定公司经营或禁止进出口的商品和技术除外），开发、生产、销售计算机软件、硬件产品，计算机应用技术咨询、培训，计算机网络系统设计、安装、维护,代办中国电信股份有限公司重庆分公司委托的电信业务。",
        "equityUrl":"http://static.tianyancha.com/equity/18f0106fdd2e27f7127ba6850dafae58.png",
        "property4":"9150000020286320X6",
        "property3":"Chang'An Auto Stock Co.,Ltd.",
        "orgNumber":"20286320X",
        "estiblishTime":846691200000,
        "regStatus":"存续",
        "bondType":"A股",
        "legalPersonName":"张宝林",
        "legalPersonId":1924407795,
        "sourceFlag":"http://qyxy.baic.gov.cn/",
        "isClaimed":0,
        "actualCapital":"",
        "websiteList":"www.changan.com.cn",
        "flag":1,
        "correctCompanyId":"",
        "email":"cazqc@changan.com.cn",
        "updateTimes":1551156180000,
        "creditCode":"9150000020286320X6",
        "bondNum":"000625",
        "weibo":"http://weibo.com/p/230677sz000625",
        "categoryScore":9194,
        "bondName":"长安汽车",
        "id":24259442,
        "regNumber":"500000000005061",
        "regCapital":"480264.851100万",
        "name":"重庆长安汽车股份有限公司",
        "approvedTime":1508774400000,
        "tags":"中国500强 : 上市公司:",
        "logo": "http://img.tianyancha.com/logo/lll/e5c8f57119ffb221418f2c32aa0fec36.png@!f_200x200",
        "taxNumber":"9150000020286320X6",
        "legalInfo":{
            "name":"张宝林",
            "hid":1924407795,
            "headUrl":"",
            "companyNum":91,
            "office":[
                {
                    "area":"山东",
                    "total":13,
                    "companyName":"淄博长安汽车销售有限责任公司",
                    "cid":2568792269,
                    "score":0,
                    "state":null
                },
                {
                    "area":"浙江",
                    "total":12,
                    "companyName":"杭州东升长安汽车销售有限公司",
                    "cid":2358924993,
                    "score":0,
                    "state":null
                },
                {
                    "area":"其他",
                    "total":66,
                    "companyName":"重庆长安汽车股份有限公司",
                    "cid":24259442,
                    "score":0,
                    "state":null
                }
            ],
            "partners":null,
            "cid":2944001620,
            "typeJoin":null
        },
        "baseInfo":"重庆长安汽车股份有限公司，简称长安汽车或重庆长安，为中国长安汽车集团股份有限公司旗下的核心整车企业，1996年在深圳证券交易所上市，A股代码000625，B股代码200625。其历史可追溯到洋务运动时期，起源于1862年的上海洋炮局，曾开创了中国近代工业的先河。1996年注册并成为极具竞争力的上市公司，拥有2家上市公司、4支股票。2014年3月重庆长安汽车股份有限公司收购合肥长安汽车有限公司。长安汽车总部位于重庆长江和嘉陵江两江汇合处，是一家开发、制造、销售全系列乘用车和商用车的汽车公司，其主要产品有全系列乘用车、小型商用车、轻型卡车、微型面包车和大中型客车，全系列发动机等，年汽车生产能力达100万辆以上，年发动机生产能力110万台以上。2015年6月3日，工信部公示2015年智能制造专项项目，94家公司的相关项目获入选，重庆长安汽车股份有限公司入围。2015年12月3日，长安汽车与高德集团成战略合作。2015年12月26日，重庆长安汽车股份有限公司召回奔奔i/奔奔LOVE车型，共30886辆车。",
        "companyOrgType":"股份有限公司(上市公司)",
        "base":"cq",
        "companyType":201,
        "companyId":500987
  },
  "result(entityType=2)": {
    "logo": "http://img.tianyancha.com/logo/lll/70f7ed38dd88a566a437de3aede00af8.png@!watermark01",
    "remarksS": "-",
    "nameEn": "Baidu （Hong Kong） Limited ",
    "companyNum": "1189285",
    "estiblishTime": 1196092800000,
    "regStatus": "仍注册",
    "entityType": 2,
    "mortgageS": "无",
    "toTime": 1196092800000,
    "id": 11364828,
    "haveReport": false,
    "companyOrgType": "私人股份有限公司",
    "name": "百度（香港）有限公司",
    "base": "hk",
    "liquidationModeS": "-",
    "importantItemsS": "-",
    "weibo": "http://weibo.com/p/230677sz000625"
  },
  "result(entityType=3)": {
    "logo": "http://img.tianyancha.com/logo/lll/a366bc14f5c51a7ea1b6c996b90e4c43.png@!watermark01",
    "regStatus": "正常",
    "legalPersonName": "陈武",
    "entityType": 3,
    "id": 2954595685,
    "businessUnit": "沈阳市工商行政管理局",
    "websiteList": "",
    "registrationDate": "2000-09-04",
    "phoneNumber": "",
    "haveReport": false,
    "regCapital": "3.00 元/万元",
    "name": "沈阳市工商行政管理学会",
    "regInstitute": "沈阳市局",
    "regLocation": "",
    "creditCode": "51210100508206173F",
    "types": "社会团体",
    "weibo": "http://weibo.com/p/230677sz000625"
  },
  "result(entityType=4)": {
    "summary": "本所是经北京市司法局核准设立的综合性律师事务所，本所注重法学理论研究，注重司法实践，擅长从事于公司法律事务等非诉讼业务，善于发挥集体协作、团队服务的优势，注重以客户利益为本的现代服务理念。在服务过程中，把客户的权益放在第一位，用丰富的法律知识与卓越的法律服务解决客户遇到的问题。具有较高的业务水准和执业经验，多年来一直担任多家大型企业、中小企业、机关团体、事业单位的常年法律顾问。",
    "phoneList": [
      "63954248"
    ],
    "permit": "21101200710240046",
    "organizationForm": "普通合伙",
    "entityType": 4,
    "id": 3077532197,
    "phoneNumber": "63954248",
    "haveReport": false,
    "regCapital": "30万元",
    "name": "北京市恒烁律师事务所",
    "regLocation": "莲花池西路16号1号楼金鑫大厦B800",
    "businessExpertise": "",
    "logo": "http://img.tianyancha.com/logo/lll/a17d41c6436ee4c75a1c8a24c28aaddb.png@!watermark01",
    "taxNumber": "",
    "headquartersBranch": "总所",
    "dateOfEstablishment": "",
    "legalPersonName": "",
    "creditRating": "",
    "websiteList": "",
    "practiceState": "正常",
    "authorities": "海淀区司法局",
    "email": "hslawfirm@163.com",
    "approvalDate": "2007-08-31",
    "creditCode": "",
    "uuid": "eec3141be44d42b7b85fe1384b8d83b8",
    "dateOfIssue": "",
    "weibo": "http://weibo.com/p/230677sz000625"
  },
  "result(entityType=5)": {
    "scope": "为社区居民提供基本医疗和基本公共卫生服务。预防保健科/全科医疗科/妇产科；妇科专业/口腔科/康复医学科/医学检验科；临床体液、血液专业；临床化学检验专业/医学影像科；Ｘ线诊断专业；超声诊断专业；心电诊断专业/中医科******。",
    "regUnitNameSecond": "",
    "regUnitName": "北京市海淀区政府公共服务委员会",
    "entityType": 5,
    "type": 1,
    "id": 3096885494,
    "haveReport": false,
    "regCapital": "600万元",
    "name": "北京市海淀区上地园区社区卫生服务中心",
    "regUnitNameThird": "",
    "regLocation": "北京市海淀区上地西路52号",
    "nameSecond": "",
    "regUnit": "北京市海淀区政府公共服务委员会",
    "expendSource": "财政补助",
    "nameThird": "",
    "logo": "http://img.tianyancha.com/logo/lll/d071d08960efa812799b158bdac16c8f.png@!watermark01",
    "usCreditCode": "12110108MB012357XN",
    "regStatus": "正常",
    "legalPersonName": "徐冬艳",
    "regUnitNameOther": "",
    "legalPersonId": 1939343073,
    "address": "北京市海淀区上地西路52号",
    "holdUnit": "北京市海淀区机构编制委员会办公室",
    "validTime": "2017-06-29至2022-06-29",
    "base": "bj",
    "oldCert": "事证第111010801079号",
    "nameOther": "",
    "weibo": "http://weibo.com/p/230677sz000625"
  },
  "result(entityType=6)": {
    "preferentialQualificationType": "--",
    "createTime": 1505290017000,
    "dataSource": "民政部门公告",
    "nationalWorkerNumber": "--",
    "scope": "全国",
    "department": "民政部",
    "historyName": "--",
    "purpose": " --",
    "type": 1,
    "entityType": 6,
    "contacts": "--",
    "id": 3078017061,
    "haveReport": false,
    "regCapital": "20,000万元",
    "orgCode": "--",
    "establishTime": "2016-07-22",
    "name": "三峡集团公益基金会",
    "regLocation": "北京市海淀区玉渊潭南路1号B座",
    "grade": "--",
    "specialFundNumber": "--",
    "logo": "http://img.tianyancha.com/logo/lll/e6d571cd52a53424167a526483406259.png@!watermark01",
    "businessScope": " --",
    "fax": "--",
    "website": "--",
    "estiblishTime": 1469116800000,
    "provinceWorkerNumber": "--",
    "postcode": "100036",
    "legalPersonName": "--",
    "contactDuty": "--",
    "legalPersonId": 0,
    "secretary": "--",
    "field": "扶贫助困，环境",
    "englishName": "Three Gorges Group Community Foundation",
    "businessUnit": "民政部",
    "address": "北京市海淀区玉渊潭南路1号B座",
    "email": "--",
    "creditCode": "53100000MJ0065049E",
    "volunteerNumber": "--",
    "employeeNumber": "--",
    "telephone": "010-57081850",
    "weibo": "http://weibo.com/p/230677sz000625"
  }
}
```

####  企业行政处罚查询返回的数据
![](https://iddc2.deloitte.com.cn/asset/images/xingzchufa.jpg)

**result 返回数据示例**
```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 1,
    "items": [
      {
        "content": "罚款0.1万元，没收违法所得和非法财物",
        "punishNumber": "德工商处字(2015)303 号",
        "regNum": "350526600032666",
        "description": null,
        "name": "德化县孙壁电器商店",
        "base": "fj",
        "decisionDate": "2015-10-14",
        "legalPersonName": "余孙壁",
        "type": "违反,对擅自销售卫星地面接收设施的行政处罚",
        "departmentName": "福建省德化县工商行政管理局",
        "publishDate": "2015-11-17"
      }
    ]
  }
}
```


####  企业分支机构查询返回的数据
![](https://iddc2.deloitte.com.cn/asset/images/fenzhijigou.jpg)

**result 返回数据示例**
```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 9,
    "items": [
      {
        "toco": 36,
        "logo": "http://img.tianyancha.com/logo/lll/8e1aa6e84ff617657c2eeadae5b451f0.png@!f_200x200",
        "alias": "百度网讯",
        "estiblishTime": 1208448000000,
        "regStatus": "存续",
        "type": 1,
        "legalPersonName": "向海龙",
        "pencertileScore": 1335,
        "legalPersonId": 1839080315,
        "id": 139572921,
        "category": "652",
        "regCapital": "",
        "name": "北京百度网讯科技有限公司深圳分公司",
        "base": "gd",
        "personType": 1
      },
      {
        "toco": 36,
        "logo": "http://img.tianyancha.com/logo/lll/e94da5a7b0bb926632ac585766028e6f.png@!f_200x200",
        "alias": "百度网讯",
        "estiblishTime": 1211212800000,
        "regStatus": "存续",
        "type": 1,
        "legalPersonName": "向海龙",
        "pencertileScore": 3835,
        "legalPersonId": 1839080315,
        "id": 139572971,
        "category": "653",
        "regCapital": "",
        "name": "北京百度网讯科技有限公司广州分公司",
        "base": "gd",
        "personType": 1
      },
      {
        "toco": 36,
        "logo": "http://img.tianyancha.com/logo/lll/762a5d7bd8f3a41a6ea39bbad6d946f0.png@!f_200x200",
        "alias": "百度网讯",
        "estiblishTime": 1210780800000,
        "regStatus": "存续",
        "type": 1,
        "legalPersonName": "向海龙",
        "pencertileScore": 3835,
        "legalPersonId": 1839080315,
        "id": 139573020,
        "category": "732",
        "regCapital": "",
        "name": "北京百度网讯科技有限公司东莞分公司",
        "base": "gd",
        "personType": 1
      },
      {
        "toco": 1,
        "logo": "http://img.tianyancha.com/logo/lll/010c44218af9a39e745a400850b48af0.png@!f_200x200",
        "alias": "百度网讯",
        "estiblishTime": 1374681600000,
        "regStatus": "存续",
        "type": 1,
        "legalPersonName": "赵坤",
        "pencertileScore": 2498,
        "legalPersonId": 2191149373,
        "id": 139573097,
        "category": "724",
        "regCapital": "",
        "name": "北京百度网讯科技有限公司南京分公司",
        "base": "js",
        "personType": 1
      }
    ]
  }
}
```


####  企业变更记录查询返回的数据
<img src="https://iddc2.deloitte.com.cn/asset/images/changerecod.jpg" style="zoom:67%;" />

**result 返回数据示例**
```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 18,
    "items": [
      {
        "changeItem": "注册资本",
        "createTime": "2017-10-27",
        "contentBefore": "8<em>9000</em>万元",
        "contentAfter": "<em>21712</em>8万元",
        "changeTime": "2017-09-07"
      },     
      {
        "changeItem": "投资人",
        "createTime": "2017-07-10",
        "contentBefore": "1 李彦宏 自然人股东2 <em>王湛</em> 自然人股东",
        "contentAfter": "1 李彦宏 自然人股东2 <em>向海龙</em> 自然人股东",
        "changeTime": "2017-07-04"
      },
      {
        "changeItem": "董事（理事）、经理、监事",
        "createTime": "2017-07-10",
        "contentBefore": "（注：标有*标志的为法定代表人）1 李彦宏 执行董事2 梁志祥* <em>总</em>经理3 <em>王湛</em> 监事",
        "contentAfter": "（注：标有*标志的为法定代表人）1 李彦宏 执行董事2 梁志祥* 经理3 <em>向海龙</em> 监事",
        "changeTime": "2017-07-04"
      }
    ]
  }
}
```



####  企业失信人查询返回的数据
<img src="https://iddc2.deloitte.com.cn/asset/images/shixinren.jpg" style="zoom:67%;" />

**result 返回数据示例**
```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 4,
    "items": [
      {
        "iname": "天津信裕房地产发展有限公司",
        "businessentity": "徐永清",
        "gistid": "【2017】津仲裁字第0330号",
        "areaname": "天津",
        "cardnum": "600563165",
        "status": "0",
        "courtname": "天津市河西区人民法院",
        "searchType": "102",
        "uni": "1f2d2908143ed9f5b380d6b3bc5b83bf",
        "publishdate": "1532275200000",
        "type": "1",
        "dishonestid": "3918023",
        "id": "196602058",
        "_type": "33",
        "disruptTypeName": "有履行能力而拒不履行生效法律文书确定义务",
        "gistunit": "天津市仲裁委员会",
        "partyTypeName": "580",
        "duty": "给付申请人10217元",
        "connList": [
          "<a href=&singlequote&https://www.tianyancha.com/company/196602058&singlequote& target=&singlequote&_blank&singlequote&>天津信裕房地产发展有限公司</a>"
        ],
        "performance": null,
        "regdate": "1519920000000",
        "eventTime": "1519920000000",
        "companyId": "3918023",
        "casecode": "(2018)津0103执1265号"
      },
      {
        "iname": "天津信裕房地产发展有限公司",
        "businessentity": "徐永清",
        "gistid": "2016津仲裁字第47号",
        "areaname": "天津",
        "courtname": "天津市河西区人民法院",
        "searchType": "102",
        "publishdate": "1501171200000",
        "type": "1",
        "dishonestid": "3918023",
        "id": "196602058",
        "_type": "33",
        "disruptTypeName": "有履行能力而拒不履行生效法律文书确定义务",
        "gistunit": "天津仲裁委员会",
        "partyTypeName": "1",
        "duty": "一、被执行人退还申请执行人购房款23515元及加倍支付迟延履行期间的债务利息681元;二、交付申请执行人案件受理费2226元、公告费1000元。",
        "connList": [
          "<a href=&singlequote&https://www.tianyancha.com/company/196602058&singlequote& target=&singlequote&_blank&singlequote&>天津信裕房地产发展有限公司</a>"
        ],
        "performance": null,
        "regdate": "1491321600000",
        "casecode": "(2017)津0103执1606号",
        "focusNumber": "0",
        "status": "0",
        "cardnum": "",
        "uni": "3211834ce11ea6d7a096bd65e731c11c",
        "companyId": "3918023",
        "eventTime": "1491321600000"
      } 
    ],
    "pageNum": 1
  }
}
```



####  企业图谱查询返回的数据
<img src="https://iddc2.deloitte.com.cn/asset/images/entermap.PNG" style="zoom:67%;" />

**result 返回数据示例**
```
{
	"error_code": 0,
	"reason": "ok",
	"result": {
		"nodes": [{
			"id": "25476889",
			"properties": {
				"aias": "口碑互联",
				"name": "北京口碑互联传媒广告有限公司",
				"logo": "http://img.tianyancha.com/logo/lll/a3ceb2e50cc56f32ebe37d65d6037424.png@!t07",
				"ntype": "f"
			},
			"labels": [
				"Company"
			]
		}],
		"relationships": [{
			"startNode": "3046112687",
			"id": "113098049",
			"type": "INVEST_C",
			"endNode": "3102575943",
			"properties": {
				"labels": [
					"参股"
				]
			}
		}]
	}
}
```

####  企业被执行人查询返回的数据
<img src="https://iddc2.deloitte.com.cn/asset/images/zhixingren.PNG" style="zoom:67%;" />

**result 返回数据示例**
```
{
	"error_code": 0,
	"reason": "ok",
	"result": {
		"total": 19,
		"items": [{
				"caseCode": "(2017)苏0812执4249号",
				"execCourtName": "淮安市清江浦区人民法院",
				"pname": "淮安禧徕乐投资发展有限公司",
				"partyCardNum": "91320811696****409A",
				"caseCreateTime": 1511107200000,
				"execMoney": "55593"
			},
			{
				"caseCode": "(2017)苏0812执4247号",
				"execCourtName": "淮安市清江浦区人民法院",
				"pname": "淮安禧徕乐投资发展有限公司",
				"partyCardNum": "69670740-9",
				"caseCreateTime": 1511107200000,
				"execMoney": "47689"
			}
		]
	}
}
```



####  企业历史工商信息查询返回的数据
<img src="https://iddc2.deloitte.com.cn/asset/images/hisgongshanginfo.jpg" style="zoom:80%;" />

**result 返回数据示例**
```
{
	"error_code": 0,
	"reason": "ok",
	"result": {
		"deadLineList": [{
			"name": "50",
			"relation": 0,
			"time": 1392652800000,
			"toco": 0,
			"type": 0
		}],
		"regNumberList": [],
		"orgNumberList": [],
		"locationList": [{
			"name": "北京市海淀区科学院南路2号融科资讯中心A座10层",
			"relation": 0,
			"time": 1453651200000,
			"toco": 0,
			"type": 0
		}],
		"historyNameList": [{
			"name": "联想控股有限公司",
			"relation": 0,
			"time": 1392652800000,
			"toco": 0,
			"type": 0
		}],
		"pastStafferList": [
			[{
				"id": 2073702832,
				"name": "王津",
				"relation": 4,
				"time": 1535558400000,
				"toco": 0,
				"type": 0
			}],
			[{
				"id": 2304997885,
				"name": "齐子鑫",
				"relation": 4,
				"time": 1517932800000,
				"toco": 0,
				"type": 0
			}],
			[{
					"id": 2074779724,
					"name": "王琪",
					"relation": 4,
					"time": 1413388800000,
					"toco": 0,
					"type": 0
				},
				{
					"id": 2317768106,
					"name": "邓麦村",
					"relation": 4,
					"time": 1413388800000,
					"toco": 0,
					"type": 0
				}
			],
			[{
					"id": 1785192175,
					"name": "余政",
					"relation": 4,
					"time": 1349971200000,
					"toco": 0,
					"type": 0
				},
				{
					"id": 1970138056,
					"name": "曾茂朝",
					"relation": 4,
					"time": 1349971200000,
					"toco": 0,
					"type": 0
				}
			]
		],
		"creditCodeList": [],
		"regCapitalList": [{
				"name": "200000万元",
				"relation": 0,
				"time": 1444406400000,
				"toco": 0,
				"type": 0
			},
			{
				"name": "66086.03994万元",
				"relation": 0,
				"time": 1392652800000,
				"toco": 0,
				"type": 0
			},
			{
				"name": "66086.03994 万元",
				"relation": 0,
				"time": 1392652800000,
				"toco": 0,
				"type": 0
			}
		],
		"typeList": [],
		"businessScopeList": [{
				"name": "项目投资；投资管理；资产管理；经济贸易咨询；投资咨询；企业管理咨询；技术开发、技术转让、技术推广；房地产开发；物业管理；销售化工产品（不含危险化学品及一类易制毒化学品）、矿产品；货物进出口、技术进出口、代理进出口；计算机系统服务；数据处理。",
				"relation": 0,
				"time": 1416412800000,
				"toco": 0,
				"type": 0
			},
			{
				"name": "法律、行政法规、国务院决定禁止的，不得经营；法律、行政法规、国务院决定规定应经许可的，经审批机关批准并经工商行政管理机关登记注册后方可经营；法律、行政法规、国务院决定未规定许可的，自主选择经营项目开展经营活动。",
				"relation": 0,
				"time": 1324310400000,
				"toco": 0,
				"type": 0
			}
		]
	}
}
```





####  企业法律诉讼查询返回的数据
![](https://iddc2.deloitte.com.cn/asset/images/falvshusong.jpg)

**result 返回数据示例**
```
{
	"error_code": 0,
	"reason": "ok",
	"result": {
		"total": 2110,
		"items": [{
				"SplitGids": "22822;1174989977;2957757725",
				"plaintiffs": "上诉人-<a href=&singlequote&https://www.tianyancha.com/company/22822&singlequote& target=&singlequote&_blank&singlequote&>北京百度网讯科技有限公司</a>",
				"plaintiffId": "",
				"court": "广州知识产权法院",
				"searchType": "101",
				"casereason": "侵害商标权纠纷",
				"uni": "88bd515103256452351d286a7a430332",
				"url": "http://wenshu.court.gov.cn/content/content?DocID=0f91b229-0327-47c1-8729-a94900a15389",
				"caseno": "（2018）粤73民辖终421号",
				"id": "239223048",
				"_type": "31",
				"docid": "0f91b229-0327-47c1-8729-a94900a15389",
				"title": "北京百度网讯科技有限公司、福州市品果源餐饮管理有限公司侵害商标权纠纷二审民事裁定书",
				"appelleeId": "1174989977",
				"abstracts": "",
				"connList": [
					"<a href=&singlequote&https://www.tianyancha.com/company/2957757725&singlequote& target=&singlequote&_blank&singlequote&>广州创业咖啡有限公司</a>",
					"<a href=&singlequote&https://www.tianyancha.com/company/22822&singlequote& target=&singlequote&_blank&singlequote&>北京百度网讯科技有限公司</a>",
					"<a href=&singlequote&https://www.tianyancha.com/company/1174989977&singlequote& target=&singlequote&_blank&singlequote&>福州市品果源餐饮管理有限公司</a>"
				],
				"submittime": "1534348800000",
				"defendantId": "2957757725",
				"lawsuitUrl": "https://www.tianyancha.com/lawsuit/7e33b29dabd311e8a8b47cd30ae00894",
				"casetype": "民事",
				"appellantId": "22822",
				"uuid": "7e33b29dabd311e8a8b47cd30ae00894",
				"eventTime": "1534348800000",
				"doctype": "民事裁定",
				"defendants": "被告-<a href=&singlequote&https://www.tianyancha.com/company/2957757725&singlequote& target=&singlequote&_blank&singlequote&>广州创业咖啡有限公司</a>，被上诉人-<a href=&singlequote&https://www.tianyancha.com/company/1174989977&singlequote& target=&singlequote&_blank&singlequote&>福州市品果源餐饮管理有限公司</a>"
			}
			=
		],
		"num": 1,
		"pageNum": 1
	}
}
```







####  企业严重违法查询返回的数据
![](https://iddc2.deloitte.com.cn/asset/images/yzweifa.jpg)

**result 返回数据示例**
```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 1,
    "items": [
      {
        "removeReason": "",
        "removeDepartment": "",
        "putDate": 1472745600000,
        "putReason": "提交虚假材料或者采取其他欺诈手段隐瞒重要事实，取得公司变更或者注销登记，被撤销登记的",
        "putDepartment": "陕西省工商行政管理局",
        "removeDate": null
      }
    ]
  }
}
```







####  企业股东信息查询返回的数据
![](https://iddc2.deloitte.com.cn/asset/images/gudong.jpg)

**result 返回数据示例**
```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 2,
    "items": [
      {
        "id": 1984012283,
        "toco": 13,
        "logo": "http://img.tianyancha.com/logo/human/2/345609db75383b411884a401a6f3665e.png@!z_200x200",
        "name": "李彦宏",
        "capitalActl": [],
        "type": 2,
        "capital": [
          {
            "amomon": "638917.36万元",
            "time": "2018-12-31",
            "percent": "99.50%",
            "paymet": "货币"
          }
        ]
      },
      {
        "id": 1839080315,
        "toco": 36,
        "logo": "http://img.tianyancha.com/logo/human2/bdfe53ae98a2256d988da372ba8d879c.png@!z_200x200",
        "name": "向海龙",
        "capitalActl": [],
        "type": 2,
        "capital": [
          {
            "amomon": "3210.64万元",
            "time": "2018-12-31",
            "percent": "0.50%",
            "paymet": "货币"
          }
        ]
      }
    ]
  }
}
```





####  企业主要人员查询返回的数据
![](https://iddc2.deloitte.com.cn/asset/images/renyuan.jpg)

**result 返回数据示例**
```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 3,
    "items": [
      {
        "toco": 12,
        "id": 2020172991,
        "typeJoin": [
          "经理"
        ],
        "logo": "http://img.tianyancha.com/logo/human2/bdb7e91f798d66661ade0c4bbb3d54bf.png@!watermark01",
        "type": 2,
        "name": "梁志祥"
      },
      {
        "toco": 8,
        "id": 1984012283,
        "typeJoin": [
          "执行董事"
        ],
        "logo": "http://img.tianyancha.com/logo/human2/345609db75383b411884a401a6f3665e.png@!watermark01",
        "type": 2,
        "name": "李彦宏"
      },
      {
        "toco": 34,
        "id": 1839080315,
        "typeJoin": [
          "监事"
        ],
        "logo": "http://img.tianyancha.com/logo/human2/bdfe53ae98a2256d988da372ba8d879c.png@!watermark01",
        "type": 2,
        "name": "向海龙"
      }
    ]
  }
}
```







####  企业经营异常查询返回的数据
![](https://iddc2.deloitte.com.cn/asset/images/jyyc.jpg)

**result 返回数据示例**
```
{
  "error_code": 0,
  "reason": "ok",
  "result": {
    "total": 2,
    "items": [
      {
        "createTime": "2017-04-09",
        "putDate": "2015-07-14",
        "removeDate": "2016-04-15",
        "removeDepartment": "长沙市工商行政管理局天心分局",
        "removeReason": "依法补报了未报年份的年度报告并公示",
        "putReason": "未按照规定报送2014年度年度报告",
        "putDepartment": "长沙市工商行政管理局天心分局"
      },
      {
        "createTime": "2017-04-09",
        "putDate": "2015-07-13",
        "removeDate": "2016-04-15",
        "removeDepartment": "长沙市工商行政管理局天心分局",
        "removeReason": "依法补报了未报年份的年度报告并公示",
        "putReason": "未按照规定报送2013年度年度报告",
        "putDepartment": "长沙市工商行政管理局天心分局"
      }
    ]
  }
}
```

####  企业搜索查询返回的数据
![](https://iddc2.deloitte.com.cn/asset/images/jyyc.jpg)

**result 返回数据示例**
```
{
	"error_code": 0,
	"reason": "ok",
	"result": {
		"items": [{
				"regNumber": "110108002734659",
				"regStatus": "在业",
				"creditCode": "91110000802100433B",
				"estiblishTime": "2001-06-05 00:00:00.0",
				"regCapital": "1342128万人民币",
				"companyType": 1,
				"name": "<em>北京百度网讯科技有限公司</em>",
				"id": 22822,
				"orgNumber": "802100433",
				"type": 1,
				"base": "北京",
				"legalPersonName": "梁志祥"
			},
			{
				"regNumber": "440106000623068",
				"regStatus": "在业",
				"creditCode": "91440101675657502F",
				"estiblishTime": "2008-05-20 00:00:00.0",
				"regCapital": "-",
				"companyType": 1,
				"name": "<em>北京百度网讯科技有限公司</em>广州分公司",
				"id": 139572971,
				"orgNumber": "675657502",
				"type": 1,
				"base": "广东",
				"legalPersonName": "沈抖"
			},			
			{
				"regNumber": "110112017796164",
				"regStatus": "在业",
				"creditCode": "911101053067230171",
				"estiblishTime": "2014-08-28 00:00:00.0",
				"regCapital": "3735.1363万人民币",
				"companyType": 1,
				"name": "<em>北京</em>太合音乐文化发展<em>有限公司</em>",
				"id": 934605,
				"orgNumber": "306723017",
				"type": 1,
				"base": "北京",
				"legalPersonName": "钱实穆"
			}
		],
		"total": 56
	}
}


```
