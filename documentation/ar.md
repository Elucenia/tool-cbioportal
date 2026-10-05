# cBioPortal: طفرات مجموعة بحثية عامة

مجموعة TCGA PanCancer العامة لسرطان الثدي، التجميع hg19. حتى 5 جينات و25 سجلًا في الصفحة. أعداد الصفحة ليست انتشارًا في المجموعة. لا يتضمن تفسيرًا علاجيًا.

## النطاق

تحليل حاسوبي لأغراض البحث. لا يحدد التشخيص أو الإمراضية أو الفعالية أو العلاج. تحقّق من المجموعة والمصدر والإصدار والنطاق قبل التفسير.

تم تنفيذ الواجهة وعقود الطلب والاستجابة داخل ELUCENIA. يعتمد التحليل على توفر الخدمة المسؤولة. لم تكتمل المراجعة السريرية المستقلة ولا المراجعة اللغوية المهنية.

## الاستعلام

- رموز الجينات
- الصفحة
- أؤكد أنني سأرسل بيانات بحثية عامة أو اصطناعية فقط، دون بيانات مرضى أو معلومات سرية.

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

تُحفظ الأسماء الرسمية للمصطلحات والمعرّفات العلمية بلغة المصدر؛ تسميات الواجهة مترجمة.

## النتائج

- الجين
- معرّف العينة العام
- التغير البروتيني
- نوع الطفرة
- الكروموسوم
- الموضع الجينومي
- الأليل المرجعي
- الأليل البديل
- السجلات في هذه الصفحة
- العينات المميزة في هذه الصفحة

يحفظ التصدير المصادر والنسب والإصدارات والحدود. تحتفظ البيانات الأصلية بترخيصها.

## الإصدار

`cBioPortal v7.1.2 · brca_tcga_pan_can_atlas_2018 · hg19`

## المصادر

تخضع بيانات cBioPortal لترخيص ODbL 1.0 ما لم ينطبق استثناء خاص بالدراسة. يجب الحفاظ على نسب البيانات إلى cBioPortal وTCGA. تتطلب إعادة توزيع قاعدة بيانات مشتقة التحقق من التزامات الترخيص.

- [https://docs.cbioportal.org/web-api-and-clients/](https://docs.cbioportal.org/web-api-and-clients/)
- [https://docs.cbioportal.org/user-guide/faq/](https://docs.cbioportal.org/user-guide/faq/)
- [https://www.cbioportal.org/api/v3/api-docs](https://www.cbioportal.org/api/v3/api-docs)
- [https://gdc.cancer.gov/about-data/publications/pancanatlas](https://gdc.cancer.gov/about-data/publications/pancanatlas)

## حدود الانتظار

الحد الزمني لكل طلب إلى هذا المزوّد هو 20 ثانية. الحد الزمني لسير العمل الكامل هو 120 ثانية، وتنتظر الواجهة 125 ثانية كحد أقصى. تتشارك الطلبات الوقت المتبقي لسير العمل. لا توجد إعادة محاولة تلقائية. إذا لم يستجب المزوّد في الوقت المحدد، ينتهي التحليل بخطأ صريح؛ ولا تُقدَّر أي نتيجة ولا تُستبدل.
