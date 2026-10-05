# cBioPortal：公开队列突变

TCGA PanCancer 乳腺癌公开队列，hg19。最多 5 个基因，每页 25 条记录。页面计数不是队列患病率。不提供治疗解释。

## 适用范围

用于研究的计算分析。不能据此确定诊断、致病性、疗效或治疗。解释前请核对人群、来源、版本与适用范围。

ELUCENIA已实现界面及请求和响应契约。分析依赖相应服务的可用性。独立临床审核和专业语言审核尚未完成。

## 查询

- 基因符号
- 页
- 我确认仅提交公开或合成研究数据，不含患者数据或保密信息。

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "type": "object",
  "properties": {
    "genes": {
      "type": "array",
      "items": {
        "type": "string",
        "pattern": "^[A-Za-z0-9][A-Za-z0-9.-]{0,31}$"
      },
      "minItems": 1,
      "maxItems": 5,
      "uniqueItems": true
    },
    "page": {
      "type": "integer",
      "minimum": 1,
      "maximum": 100
    },
    "publicResearchData": {
      "const": true,
      "description": "Only public or synthetic research inputs; no patient/confidential data."
    }
  },
  "required": [
    "genes",
    "page",
    "publicResearchData"
  ],
  "additionalProperties": false
}
```

官方术语名称和科学标识符保留来源语言；界面标签已翻译。

## 结果

- 基因
- 公开样本标识符
- 蛋白质变化
- 突变类型
- 染色体
- 基因组位置
- 参考等位基因
- 替代等位基因
- 本页记录数
- 本页不同样本数

导出保留来源、署名、版本和限制。原始数据保留其许可证。

## 版本

`cBioPortal v7.1.2 · brca_tcga_pan_can_atlas_2018 · hg19`

## 来源

cBioPortal数据使用ODbL 1.0，除非具体研究另有例外。请保留cBioPortal和TCGA署名。重新分发衍生数据库时须核对许可义务。

- [https://docs.cbioportal.org/web-api-and-clients/](https://docs.cbioportal.org/web-api-and-clients/)
- [https://docs.cbioportal.org/user-guide/faq/](https://docs.cbioportal.org/user-guide/faq/)
- [https://www.cbioportal.org/api/v3/api-docs](https://www.cbioportal.org/api/v3/api-docs)
- [https://gdc.cancer.gov/about-data/publications/pancanatlas](https://gdc.cancer.gov/about-data/publications/pancanatlas)

## 等待时限

向此服务提供方发送的每个请求限时 20 秒。整个工作流程限时 120 秒，界面最多等待 125 秒。各请求共享工作流程的剩余时间。不会自动重试。如果服务提供方未及时响应，分析将以明确的错误结束；不会估算或替换任何结果。
