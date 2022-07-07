# Amazon_Textract_Extract_text_key_value_pair_tables

Amazon Textract makes it easy to add document text detection and analysis to your applications. Using Amazon Textract customers can:

Detect typed and handwritten text in a variety of documents, including financial reports, medical records, and tax forms.

Extract text, forms, and tables from documents with structured data, using the Amazon Textract Document Analysis API.

Specify and extract information from documents using the Queries feature within the Amazon Textract Analyze Document API.

Process invoices and receipts with the AnalyzeExpense API.

Process ID documents such as drivers licenses and passports issued by U.S. government, using the AnalyzeID API.

Amazon Textract is based on the same proven, highly scalable, deep-learning technology that was developed by Amazon's computer vision scientists to analyze billions of images and videos daily. You don't need any machine learning expertise to use it. Amazon Textract includes simple, easy-to-use APIs that can analyze image files and PDF files. Amazon Textract is always learning from new data, and Amazon is continually adding new features to the service.

Amazon Textract analyzes documents and forms for relationships among detected text. Amazon Textract analysis operations return 4 categories of document extraction — text, forms, tables and query responses. The analysis of invoices and receipts is handled through a different process, for more information see Analyzing Invoices and Receipts.

Text Extraction

The raw text extracted from a document. For more information, see Lines and words of text.

Form Extraction

Form data is linked to text items extracted from a document. Amazon Textract represents form data as key-value pairs. In the following example, one of the lines of text detected by Amazon Textract is Name: Jane Doe. Amazon Textract also identifies a key (Name:) and a value (Jane Doe). For more information, see Form data (Key-value pairs).

Name: Jane Doe

Address: 123 Any Street, Anytown, USA

Birth date: 12-26-1980

Key-value pairs are also used to represent check boxes or option buttons (radio buttons) that are extracted from forms.

Male: ☑

For more information, see Selection elements.

Table Extraction

Amazon Textract can extract tables, table cells, and the items within table cells and may be programmed to return the results in a JSON, .csv, or a .txt file.

Name	Address
Ana Carolina

123 Any Town

For more information, see Tables. Selection elements can also be extracted from tables. For more information, see Selection elements.

Queries in Document Analysis

When processing a document with Amazon Textract, you may add queries to your analysis to specify what information you need. This involves passing a question, such as "What is the customer's social security number?" to Amazon Textract. Amazon Textract will then find the information in the document for that question and return it in a response structure separate from the rest of the document's information. For more information about this response structure, see Query Response Structures. For more information on best practices for query use, see Best Practices for Queries. Queries can be processed alone, or in combination with any other FeatureType, such as Tables or Forms.

Example Query: What is the customer’s SSN?

Example Answer: 111-xx-333

For analyzed items, Amazon Textract returns the following in multiple Block objects:

The lines and words of detected text

The content of detected items

The relationship between detected items

The page that the item was detected on

The location of the item on the document page

You can use synchronous or asynchronous operations to analyze text in a document. To analyze text synchronously, use the AnalyzeDocument operation, and pass a document as input. AnalyzeDocument returns the entire set of results. For more information, see Analyzing Document Text with Amazon Textract.

To detect text asynchronously, use StartDocumentAnalysis to start processing. To get the results, call GetDocumentAnalysis. The results are returned in one or more responses from GetDocumentAnalysis. For more information and an example, see Detecting or Analyzing Text in a Multipage Document.

To specify which type of analysis to perform, you can use the FeatureTypes list input parameter. Add TABLES to the list to return information about the tables that are detected in the input document—for example, table cells, cell text, and selection elements in cells. Add FORMS to return word relationships, such as key-value pairs and selection elements. Add QUERIES specify information you want Amazon Textract to look for in the document and get a response back in the form of a question-answer pair. To perform all types of analysis, add TABLES, FORMS and QUERIES to FeatureTypes.

All lines and words that are detected in the document are included in the response (including text not related to the value of FeatureTypes).
