---
editable: false
sourcePath: en/_api-ref/ai/ocr/v1/ocr/api-ref/TextRecognition/recognize.md
---

# Vision OCR API, REST: TextRecognition.recognize
To send the image for text recognition.
 

 
## HTTP request {#https-request}
```
POST https://ocr.{{ api-host }}/ocr/v1/recognizeText
```
 
## Body parameters {#body_params}
 
```json 
{
  "mimeType": "string",
  "languageCodes": [
    "string"
  ],
  "model": "string",
  "content": "string"
}
```

 
Field | Description
--- | ---
mimeType | **string**<br><p>Specifications of the (<a href="https://en.wikipedia.org/wiki/Media_type">MIME type</a>). Each specification contains the file to analyze and features to use for analysis. Restrictions:</p> <ul> <li>Supported file formats: ``JPEG``, ``PNG``, ``WEBP``, ``PDF``.</li> <li>Maximum file size: 20 MB.</li> <li>Image size should not exceed 20M pixels (length x width).</li> <li>The number of pages in a PDF file should not exceed 200 (each page counts as 1 request).</li> </ul> 
languageCodes[] | **string**<br><p>List of the languages to recognize text. Specified in <a href="https://en.wikipedia.org/wiki/ISO_639-1">ISO 639-1</a> format (for example, ``ru``).</p> 
model | **string**<br><p>Model to use for text detection. The maximum string length is 50 characters. Possible values:</p> <ul> <li>``page`` (default): this model is suitable for detecting multiple text entries in an image.</li> <li>``passport``: passport, the main double-page spread.</li> <li>``driver-license-front``: driver's license, the front side.</li> <li>``driver-license-back``: driver's license, the reverse side.</li> <li>``vehicle-registration-front``: front side of the vehicle registration certificate.</li> <li>``vehicle-registration-back``: back side of the vehicle registration certificate.</li> </ul> <p>The maximum string length in characters is 50.</p> 
content | **string** (byte)<br><p>Bytes with data</p> 
 
## Response {#responses}
**HTTP Code: 200 - OK**

```json 
{
  "textAnnotation": {
    "width": "string",
    "height": "string",
    "blocks": [
      {
        "boundingBox": {
          "vertices": [
            {
              "x": "string",
              "y": "string"
            }
          ]
        },
        "lines": [
          {
            "boundingBox": {
              "vertices": [
                {
                  "x": "string",
                  "y": "string"
                }
              ]
            },
            "text": "string",
            "words": [
              {
                "boundingBox": {
                  "vertices": [
                    {
                      "x": "string",
                      "y": "string"
                    }
                  ]
                },
                "text": "string",
                "entityIndex": "string"
              }
            ]
          }
        ],
        "languages": [
          {
            "languageCode": "string"
          }
        ]
      }
    ],
    "entities": [
      {
        "name": "string",
        "text": "string"
      }
    ]
  },
  "page": "string"
}
```

 
Field | Description
--- | ---
textAnnotation | **object**<br><p>Recognized text blocks in this page or text from entities.</p> 
textAnnotation.<br>width | **string** (int64)<br><p>Page width in pixels.</p> 
textAnnotation.<br>height | **string** (int64)<br><p>Page height in pixels.</p> 
textAnnotation.<br>blocks[] | **object**<br><p>Recognized text blocks in this page.</p> 
textAnnotation.<br>blocks[].<br>boundingBox | **object**<br><p>Area on the page where the text block is located.</p> 
textAnnotation.<br>blocks[].<br>boundingBox.<br>vertices[] | **object**<br><p>The bounding polygon vertices.</p> 
textAnnotation.<br>blocks[].<br>boundingBox.<br>vertices[].<br>x | **string** (int64)<br><p>X coordinate in pixels.</p> 
textAnnotation.<br>blocks[].<br>boundingBox.<br>vertices[].<br>y | **string** (int64)<br><p>Y coordinate in pixels.</p> 
textAnnotation.<br>blocks[].<br>lines[] | **object**<br><p>Recognized lines in this block.</p> 
textAnnotation.<br>blocks[].<br>lines[].<br>boundingBox | **object**<br><p>Area on the page where the line is located.</p> 
textAnnotation.<br>blocks[].<br>lines[].<br>boundingBox.<br>vertices[] | **object**<br><p>The bounding polygon vertices.</p> 
textAnnotation.<br>blocks[].<br>lines[].<br>boundingBox.<br>vertices[].<br>x | **string** (int64)<br><p>X coordinate in pixels.</p> 
textAnnotation.<br>blocks[].<br>lines[].<br>boundingBox.<br>vertices[].<br>y | **string** (int64)<br><p>Y coordinate in pixels.</p> 
textAnnotation.<br>blocks[].<br>lines[].<br>text | **string**<br><p>Recognized text.</p> 
textAnnotation.<br>blocks[].<br>lines[].<br>words[] | **object**<br><p>Recognized words</p> 
textAnnotation.<br>blocks[].<br>lines[].<br>words[].<br>boundingBox | **object**<br><p>Area on the page where the word is located.</p> 
textAnnotation.<br>blocks[].<br>lines[].<br>words[].<br>boundingBox.<br>vertices[] | **object**<br><p>The bounding polygon vertices.</p> 
textAnnotation.<br>blocks[].<br>lines[].<br>words[].<br>boundingBox.<br>vertices[].<br>x | **string** (int64)<br><p>X coordinate in pixels.</p> 
textAnnotation.<br>blocks[].<br>lines[].<br>words[].<br>boundingBox.<br>vertices[].<br>y | **string** (int64)<br><p>Y coordinate in pixels.</p> 
textAnnotation.<br>blocks[].<br>lines[].<br>words[].<br>text | **string**<br><p>Recognized word value.</p> 
textAnnotation.<br>blocks[].<br>lines[].<br>words[].<br>entityIndex | **string** (int64)<br><p>ID of the recognized word in entities array.</p> 
textAnnotation.<br>blocks[].<br>languages[] | **object**<br><p>A list of detected languages</p> 
textAnnotation.<br>blocks[].<br>languages[].<br>languageCode | **string**<br><p>Detected language code.</p> 
textAnnotation.<br>entities[] | **object**<br><p>Recognized entities.</p> 
textAnnotation.<br>entities[].<br>name | **string**<br><p>Entity name.</p> 
textAnnotation.<br>entities[].<br>text | **string**<br><p>Recognized entity text.</p> 
page | **string** (int64)<br><p>Page number in PDF file.</p> 