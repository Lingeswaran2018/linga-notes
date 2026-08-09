                    OCR Layer
                ┌─────────────────┐
                │ PaddleOCR-VL    │
                └────────┬────────┘
                         │
                         ▼
                 Structured JSON
                         │
        ┌────────────────┴────────────────┐
        │                                 │
        ▼                                 ▼
   JSON Validator                  Image Metadata
        │
        ▼
   Document Parser
        │
 ┌──────┼──────────────┬───────────────┐
 ▼      ▼              ▼               ▼
Tables Paragraphs  Images/Figures   Formulas
 │
 ▼
Table Parser
 │
 ▼
Pandas DataFrame
 │
 ┌───────────────┬─────────────┬─────────────┐
 ▼               ▼             ▼             ▼
CSV            Excel        Database        REST API


# project structure
ocr_project/
│
├── app.py
│
├── config.py
│
├── images/
│
├── output/
│
├── parser/
│   ├── document_parser.py
│   ├── table_parser.py
│   ├── paragraph_parser.py
│   ├── image_parser.py
│   └── formula_parser.py
│
├── exporters/
│   ├── csv_exporter.py
│   ├── excel_exporter.py
│   ├── json_exporter.py
│   ├── database_exporter.py
│   └── api_exporter.py
│
├── models/
│
└── utils/


# final plan

pdf-table-extractor/
│
├── app.py                     # FastAPI entry point
├── requirements.txt
├── README.md
├── .env
│
├── config/
│   ├── settings.py
│   ├── constants.py
│   └── logging.py
│
├── api/
│   ├── routes/
│   │   ├── extract.py
│   │   ├── health.py
│   │   └── download.py
│   │
│   ├── schemas/
│   │   ├── request.py
│   │   └── response.py
│   │
│   └── dependencies.py
│
├── core/
│   ├── paddle_engine.py
│   ├── pdf_processor.py
│   ├── page_processor.py
│   └── pipeline.py
│
├── parsers/
│   ├── document_parser.py
│   ├── table_parser.py
│   ├── text_parser.py
│   └── json_parser.py
│
├── exporters/
│   ├── excel_exporter.py
│   ├── csv_exporter.py
│   ├── json_exporter.py
│   └── zip_exporter.py
│
├── services/
│   ├── extraction_service.py
│   ├── export_service.py
│   └── storage_service.py
│
├── models/
│   ├── document.py
│   ├── page.py
│   └── table.py
│
├── utils/
│   ├── file_utils.py
│   ├── pdf_utils.py
│   └── dataframe_utils.py
│
├── storage/
│   ├── uploads/
│   ├── temp/
│   └── output/
│
└── tests/
    ├── test_parser.py
    ├── test_exporter.py
    └── test_api.py


# plan
PDF

↓

Split into Pages

↓

Page 1
Page 2
Page 3
...

↓

PaddleOCR-VL

↓

JSON

↓

Extract Tables

↓

DataFrame

↓

Export