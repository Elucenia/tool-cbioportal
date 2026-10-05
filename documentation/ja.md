# cBioPortal：公開コホートの変異

TCGA PanCancer の乳がん公開コホート、hg19。最大5遺伝子、1ページ25件。ページ内の件数はコホート有病率ではありません。治療上の解釈は含みません。

## 適用範囲

研究用の計算解析です。診断、病原性、有効性、治療を確定するものではありません。解釈前に対象集団、出典、バージョン、範囲を確認してください。

ELUCENIA内に画面とリクエスト・レスポンスの契約を実装しています。解析には提供元サービスの稼働が必要です。独立した臨床レビューと専門家による言語レビューは完了していません。

## クエリ

- 遺伝子シンボル
- ページ
- 患者データや機密情報を含まない、公開または合成の研究データのみを送信することを確認します。

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

公式の用語名と科学的識別子は情報源の言語を保持します。インターフェースのラベルは翻訳済みです。

## 結果

- 遺伝子
- 公開サンプル識別子
- タンパク質の変化
- 変異の種類
- 染色体
- ゲノム上の位置
- 参照アレル
- 代替アレル
- このページの件数
- このページの異なるサンプル数

エクスポートには出典、帰属、バージョン、制限を保持します。原データのライセンスは引き継がれます。

## バージョン

`cBioPortal v7.1.2 · brca_tcga_pan_can_atlas_2018 · hg19`

## 情報源

cBioPortalのデータは、研究固有の例外がない限りODbL 1.0に従います。cBioPortalとTCGAの出典表示を保持してください。派生データベースを再配布する際は、ライセンス上の義務を確認する必要があります。

- [https://docs.cbioportal.org/web-api-and-clients/](https://docs.cbioportal.org/web-api-and-clients/)
- [https://docs.cbioportal.org/user-guide/faq/](https://docs.cbioportal.org/user-guide/faq/)
- [https://www.cbioportal.org/api/v3/api-docs](https://www.cbioportal.org/api/v3/api-docs)
- [https://gdc.cancer.gov/about-data/publications/pancanatlas](https://gdc.cancer.gov/about-data/publications/pancanatlas)

## 待機時間の上限

この提供元への各リクエストの上限は20秒です。処理全体の上限は120秒で、画面は最大125秒待機します。各リクエストは処理全体の残り時間を共有します。自動再試行は行いません。提供元が時間内に応答しない場合、分析は明示的なエラーで終了し、結果の推定や代替は行いません。
