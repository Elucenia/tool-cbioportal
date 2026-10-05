# cBioPortal: सार्वजनिक समूह की उत्परिवर्तन जानकारी

TCGA PanCancer का सार्वजनिक स्तन-कैंसर समूह, hg19। अधिकतम 5 जीन और प्रति पृष्ठ 25 रिकॉर्ड। पृष्ठ की गिनती समूह में प्रसार नहीं है। उपचार संबंधी व्याख्या शामिल नहीं है।

## दायरा

अनुसंधान के लिए संगणकीय विश्लेषण। यह निदान, रोगजनकता, प्रभावकारिता या उपचार निर्धारित नहीं करता। व्याख्या से पहले जनसमूह, स्रोत, संस्करण और दायरा जाँचें।

ELUCENIA में इंटरफ़ेस और अनुरोध तथा प्रतिक्रिया अनुबंध लागू हैं। विश्लेषण संबंधित सेवा की उपलब्धता पर निर्भर है। स्वतंत्र नैदानिक समीक्षा और पेशेवर भाषा समीक्षा पूरी नहीं हुई हैं।

## प्रश्न

- जीन प्रतीक
- पृष्ठ
- मैं पुष्टि करता हूँ कि केवल सार्वजनिक या कृत्रिम अनुसंधान डेटा भेजूँगा, जिसमें रोगी या गोपनीय डेटा नहीं होगा।

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

आधिकारिक शब्द-नाम और वैज्ञानिक पहचानकर्ता स्रोत की भाषा में सुरक्षित रहते हैं; इंटरफ़ेस के लेबल अनूदित हैं।

## परिणाम

- जीन
- सार्वजनिक नमूना पहचानकर्ता
- प्रोटीन परिवर्तन
- उत्परिवर्तन प्रकार
- गुणसूत्र
- जीनोम में स्थान
- संदर्भ एलील
- वैकल्पिक एलील
- इस पृष्ठ पर रिकॉर्ड
- इस पृष्ठ पर अलग-अलग नमूने

निर्यात में स्रोत, श्रेय, संस्करण और सीमाएँ सुरक्षित रहते हैं। मूल डेटा का लाइसेंस बना रहता है।

## संस्करण

`cBioPortal v7.1.2 · brca_tcga_pan_can_atlas_2018 · hg19`

## स्रोत

cBioPortal डेटा ODbL 1.0 के अंतर्गत है, जब तक अध्ययन का कोई विशेष अपवाद न हो। cBioPortal और TCGA का श्रेय बनाए रखें। किसी व्युत्पन्न डेटाबेस के पुनर्वितरण से पहले लाइसेंस के दायित्व जाँचना आवश्यक है।

- [https://docs.cbioportal.org/web-api-and-clients/](https://docs.cbioportal.org/web-api-and-clients/)
- [https://docs.cbioportal.org/user-guide/faq/](https://docs.cbioportal.org/user-guide/faq/)
- [https://www.cbioportal.org/api/v3/api-docs](https://www.cbioportal.org/api/v3/api-docs)
- [https://gdc.cancer.gov/about-data/publications/pancanatlas](https://gdc.cancer.gov/about-data/publications/pancanatlas)

## प्रतीक्षा की समय-सीमाएँ

इस प्रदाता को भेजे गए हर अनुरोध की सीमा 20 सेकंड है। पूरी कार्यप्रक्रिया की सीमा 120 सेकंड है; इंटरफ़ेस अधिकतम 125 सेकंड प्रतीक्षा करता है। सभी अनुरोध कार्यप्रक्रिया का बचा हुआ समय साझा करते हैं। अपने-आप दोबारा प्रयास नहीं किया जाता। यदि प्रदाता समय पर जवाब नहीं देता, तो विश्लेषण स्पष्ट त्रुटि के साथ समाप्त होता है; किसी परिणाम का अनुमान नहीं लगाया जाता और न ही कोई वैकल्पिक परिणाम दिया जाता।
